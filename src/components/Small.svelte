<script>
  export let title;
  export let type = "";
</script>

<style>
  .small {
    font-size: 12px;
    color: var(--text);
  }
  .error {
    color: var(--primary);
    font-size: 12px;
    padding-top: 8px;
    font-weight: 600;
  }
</style>

<p class="small {type}">{title}</p>
