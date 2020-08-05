<script>
  import Logo from "../components/Logo.svelte";
</script>

<style>
  main {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    min-height: 80vh;
    text-align: center;
  }
</style>

<main>
  <Logo title="Sign up" subtitle="Create your Pluoro account" />
  <div>Sign up</div>

  <a href="/account/sign-in">Sign in</a>
  <a href="/?im=ivan" tinro-ignore>Home</a>
</main>
