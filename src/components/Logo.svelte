<script>
  export let title;
  export let subtitle;
</script>

<style>
  .logo {
    cursor: pointer;
    display: flex;
    flex-direction: column;
    align-items: center;
    text-decoration: none;
  }
  .logo img {
    width: 100px;
  }
  .logo-text-primary {
    text-decoration: none;
    font-weight: 500;
    font-size: 26px;
    color: var(--primary);
    display: inline-block;
    padding: 0;
    letter-spacing: 1px;
    margin: 15px 0px 20px 0px;
  }
  .logo-text-secondary {
    display: block;
    color: var(--neutral);
    margin-bottom: 15px;
  }
</style>

<a href="/account" class="logo">
  <img src="/static/logo.png" alt="logo" />
  <div>
    <div class="logo-text-primary">{title}</div>
    <div class="logo-text-secondary">{subtitle}</div>
  </div>
</a>
