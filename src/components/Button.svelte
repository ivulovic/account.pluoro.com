<script>
  export let title;
</script>

<style>
  .button {
    border: none;
    outline: none;
    background: transparent;
    font-size: 16px;
    font-weight: 600;
    text-decoration: none;
    font-size: 0.875rem;
    border-radius: 4px;
    letter-spacing: 0.25px;
  }
  .primary {
    background: var(--primary);
    color: #fefefe;
    padding: 12px 16px;
    cursor: pointer;
    transition: all 0.5s ease;
  }
  .primary:hover,
  .primary:focus {
    background: var(--text);
  }
</style>

<button on:click type="button" class="button primary">{title}</button>
