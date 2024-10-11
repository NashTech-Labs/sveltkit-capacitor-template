<script>
    import { createEventDispatcher } from 'svelte';
  
    const dispatch = createEventDispatcher();
  
    let name = '';
    let email = '';
    let dob = '';
  
    function handleSubmit(event) {
      event.preventDefault();
      const userData = { name, email, dob };
      dispatch('submit', userData);
    }
  </script>
  
  <form on:submit={handleSubmit}>
    <div class="form-group">
      <label for="name">Name:</label>
      <input type="text" id="name" bind:value={name} required>
    </div>
    <div class="form-group">
      <label for="email">Email:</label>
      <input type="email" id="email" bind:value={email} required>
    </div>
    <div class="form-group">
      <label for="dob">Date of Birth:</label>
      <input type="date" id="dob" bind:value={dob} required>
    </div>
    <button type="submit">Submit</button>
  </form>
  
  <style>
    form {
      display: flex;
      flex-direction: column;
      gap: 1rem;
    }
  
    .form-group {
      display: flex;
      flex-direction: column;
    }
  
    label {
      margin-bottom: 0.5rem;
    }
  
    input {
      padding: 0.5rem;
      border: 1px solid #ccc;
      border-radius: 4px;
    }
  
    button {
      background-color: #0066cc;
      color: white;
      border: none;
      padding: 0.5rem 1rem;
      border-radius: 4px;
      cursor: pointer;
    }
  
    button:hover {
      background-color: #0052a3;
    }
  
    @media (max-width: 768px) {
      input {
        font-size: 16px; /* Prevents zoom on mobile devices */
      }
    }
  </style>