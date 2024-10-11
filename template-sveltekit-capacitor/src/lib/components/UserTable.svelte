<script>
  export let users = [];
</script>

<div class="table-container">
  <table>
    <thead>
      <tr>
        <th>Name</th>
        <th>Email</th>
        <th>Date of Birth</th>
      </tr>
    </thead>
    <tbody>
      {#each users as user}
        <tr>
          <td>{user.name}</td>
          <td>{user.email}</td>
          <td>{new Date(user.dob).toLocaleDateString()}</td>
        </tr>
      {/each}
    </tbody>
  </table>
</div>

<style>
  .table-container {
    overflow-x: auto;
  }

  table {
    width: 100%;
    border-collapse: collapse;
    margin-top: 1rem;
  }

  th,
  td {
    border: 1px solid #ccc;
    padding: 0.5rem;
    text-align: left;
  }

  th {
    background-color: #f0f0f0;
  }

  @media (max-width: 768px) {
    th,
    td {
      padding: 0.25rem;
    }
  }
</style>
