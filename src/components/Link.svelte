<script>
  export let href;
  export let title;
</script>

<style>
  .link {
    color: var(--link);
    cursor: pointer;
    display: inline-block;
    text-decoration: none;
    font-weight: 600;
    letter-spacing: 0.25px;
    line-height: 36px;
    padding: 3px 9px;
    margin-left: -9px;
    font-size: 14px;
    position: relative;
    transition: background 0.3s ease;
    outline: none;
    border-radius: 4px;
  }
  .link:hover,
  .link:focus {
    background: var(--edge);
    opacity: 1;
  }
</style>

<a class="link" {href}>{title}</a>
