<script>
  import { onMount } from "svelte";
  import Header from "$lib/components/Header.svelte";
  import Footer from "$lib/components/Footer.svelte";
  import Modal from "$lib/components/Modal.svelte";
  import UserForm from "$lib/components/UserForm.svelte";
  import UserTable from "$lib/components/UserTable.svelte";
  import { Http } from "@capacitor-community/http";
  import { Capacitor } from "@capacitor/core";

  let showModal = false;
  let users = [];

  const API_URL = "http://127.0.0.1:3000/api";

  onMount(async () => {
    console.log("API URL:", API_URL);
    try {
      if (Capacitor.isNativePlatform()) {
        // Native mobile platform
        const response = await Http.request({
          method: "GET",
          url: `http://10.0.2.2:3000/api/users`,
          params: {},
          headers: {
            "Content-Type": "application/json",
          },
        });
        console.log(response.data);
        users = response.data;
      } else {
        const response = await fetch(`${API_URL}/users`);
        if (response.ok) {
          users = await response.json();
          console.log(users);
        } else {
          console.log("failed", response);
        }
      }
    } catch (error) {
      console.log("failed due to error", error);
    }
  });

  function toggleModal() {
    showModal = !showModal;
  }

  async function handleFormSubmit(userData) {
    console.log(userData);
    try {
      if (Capacitor.isNativePlatform()) {
        // Native mobile platform (Android/iOS)
        const response = await Http.request({
          method: "POST",
          url: `http://10.0.2.2:3000/api/users`,
          headers: {
            "Content-Type": "application/json",
          },
          data: userData,
          params: {},
        });
        const newUser = await response.data;
        users = [...users, newUser];
        showModal = false;
      } else {
        const response = await fetch(`${API_URL}/users`, {
          method: "POST",
          headers: {
            "Content-Type": "application/json",
          },
          body: JSON.stringify(userData),
        });

        if (response.ok) {
          console.log("API call successful:", response);
          const newUser = await response.json();
          users = [...users, newUser];
          showModal = false;
        } else {
          console.log("API call failed:", response);
        }
      }
    } catch (error) {
      console.error("API call error:", error);
    }
  }
</script>

<Header />

<main>
  <h1>Welcome to My SvelteKit App</h1>
  <button on:click={toggleModal}>Add User</button>
  <UserTable {users} />
</main>

<Modal {showModal} on:close={toggleModal}>
  <UserForm on:submit={(e) => handleFormSubmit(e.detail)} />
</Modal>

<Footer />

<style>
  main {
    max-width: 800px;
    margin: 2rem auto;
    padding: 0 1rem;
  }

  button {
    background-color: #0066cc;
    color: white;
    border: none;
    padding: 0.5rem 1rem;
    border-radius: 4px;
    cursor: pointer;
    margin-bottom: 1rem;
  }

  button:hover {
    background-color: #0052a3;
  }

  @media (max-width: 768px) {
    main {
      padding: 0 0.5rem;
    }
  }
</style>
