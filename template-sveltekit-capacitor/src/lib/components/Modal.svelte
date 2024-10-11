<script>
  export let showModal = false;
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  function closeModal() {
    dispatch("close");
  }
</script>

{#if showModal}
  <div class="modal-backdrop" on:click={closeModal}>
    <div class="modal-content" on:click|stopPropagation>
      <button class="close-button" on:click={closeModal}>&times;</button>
      <slot></slot>
    </div>
  </div>
{/if}

<style>
  .modal-backdrop {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 1000;
  }

  .modal-content {
    background-color: white;
    padding: 2rem;
    border-radius: 4px;
    max-width: 90%;
    max-height: 90%;
    overflow-y: auto;
    position: relative;
  }

  .close-button {
    position: absolute;
    top: 0.5rem;
    right: 0.5rem;
    background: none;
    border: none;
    font-size: 1.5rem;
    cursor: pointer;
  }

  @media (max-width: 768px) {
    .modal-content {
      padding: 1rem;
    }
  }
</style>
