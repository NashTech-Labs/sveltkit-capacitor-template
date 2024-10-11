<script>
  import "../app.css";
</script>

<slot />

<style>
  :global(body) {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    min-height: 100vh;
    position: relative;
    padding-bottom: 60px; /* Height of the footer */
  }
</style>
