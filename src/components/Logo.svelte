<script>
  export let title;
  export let subtitle;
</script>

<style>
  .logo {
    display: flex;
    flex-direction: column;
    text-decoration: none;
    width: 100%;
    text-align: center;
  }
  .logo img {
    width: 50px;
    margin: 0 auto;
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
    color: var(--text);
    font-size: 16px;
    font-weight: 400;
    letter-spacing: 0.1px;
    line-height: 1.5;
  }
</style>

<div class="logo">
  <img src="/static/logo.png" alt="logo" />
  <div>
    <div class="logo-text-primary">{title}</div>
    <div class="logo-text-secondary">{subtitle}</div>
  </div>
</div>
