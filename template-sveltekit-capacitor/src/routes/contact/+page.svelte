<script>
  import Header from "$lib/components/Header.svelte";
  import Footer from "$lib/components/Footer.svelte";
</script>

<Header />

<main>
  <h1>Contact Us</h1>
  <p>
    This is the contact page of our SvelteKit application. Feel free to reach
    out to us using the information below:
  </p>
  <ul>
    <li>Email: contact@example.com</li>
    <li>Phone: (123) 456-7890</li>
    <li>Address: 123 Main St, Anytown, USA</li>
  </ul>
</main>

<Footer />

<style>
  main {
    max-width: 800px;
    margin: 2rem auto;
    padding: 0 1rem;
  }

  ul {
    list-style-type: none;
    padding: 0;
  }

  li {
    margin-bottom: 0.5rem;
  }
</style>
