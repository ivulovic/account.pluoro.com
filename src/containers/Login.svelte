<script>
  import Logo from "../components/Logo.svelte";
  import { setCookie } from "../utils/cookie";
  import Button from "../components/Button.svelte";
  import Input from "../components/Input.svelte";
  import Link from "../components/Link.svelte";
  let username = "";
  let password = "";
  function redirectToHome() {
    setCookie("TestAuthorization", "simple", 8);
    window.location.href = "/";
  }
  function handleSubmit() {
    alert("Sign in " + username + " " + password);
  }
</script>

<style>
  main {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    min-height: 100vh;
    max-width: 400px;
    width: 100%;
    margin: 0 auto;
  }
  .form {
    margin: 25px 0px;
    width: 100%;
    text-align: start;
    display: grid;
    grid-row-gap: 25px;
  }
  .input-row {
    width: 100%;
    display: flex;
    flex-direction: column-reverse;
  }
  .text-right {
    text-align: right;
  }
  .row-two {
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-column-gap: 25px;
  }
</style>

<main>
  <Logo title="Sign in" subtitle="Use your Pluoro account" />

  <div class="form">
    <div>
      <Input
        id="usernameOrEmail"
        on:change={(e) => {
          username = e.target.value;
        }}
        value={username}
        label="Username or E-mail" />
    </div>
    <div class="input-row">
      <Input
        id="password"
        type="password"
        on:change={(e) => {
          password = e.target.value;
        }}
        value={password}
        label="Password" />
    </div>
    <div class="row-two">
      <div>
        <Link href="/account/sign-up" title="Create account" />
      </div>
      <div class="text-right">
        <Button title="Sign in" on:click={handleSubmit} />
      </div>
    </div>
  </div>
  <!-- <button on:click={redirectToHome}>OK</button> -->

</main>
