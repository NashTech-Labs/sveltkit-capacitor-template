<script>
  import Header from "$lib/components/Header.svelte";
  import Footer from "$lib/components/Footer.svelte";
</script>

<Header />

<main>
  <h1>About Us</h1>
  <p>
    This is the about page of our SvelteKit application. Here you can learn more
    about our company, mission, and values.
  </p>
</main>

<Footer />

<style>
  main {
    max-width: 800px;
    margin: 2rem auto;
    padding: 0 1rem;
  }
</style>
