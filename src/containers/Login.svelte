<script>
  import Logo from "../components/Logo.svelte";
  import { setCookie } from "../utils/cookie";
  function redirectToHome() {
    setCookie("TestAuthorization", "simple", 8);
    window.location.href = "/";
  }
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
  <Logo title="Sign in" subtitle="Use your Pluoro account" />
  <div>Sign in</div>
  <button on:click={redirectToHome}>OK</button>

  <a href="/account/sign-up">Sign up instead</a>
</main>
