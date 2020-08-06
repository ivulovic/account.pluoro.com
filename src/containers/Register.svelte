<script>
  import Logo from "../components/Logo.svelte";
  import { setCookie } from "../utils/cookie";
  import Button from "../components/Button.svelte";
  import Input from "../components/Input.svelte";
  import Link from "../components/Link.svelte";
  import Small from "../components/Small.svelte";
  let firstName = "";
  let lastName = "";
  let email = "";
  let password = "";
  let confirmPassword = "";
  function redirectToHome() {
    setCookie("TestAuthorization", "simple", 8);
    window.location.href = "/";
  }
  function handleSubmit() {
    alert(
      "Sign up " +
        firstName +
        " " +
        lastName +
        " " +
        email +
        " " +
        " " +
        password +
        " " +
        confirmPassword
    );
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
    text-align: start;
    display: grid;
    grid-row-gap: 25px;
    margin: 25px 0px;
  }
  .input-row {
    display: flex;
    flex-direction: column-reverse;
  }
  .row-two {
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-column-gap: 35px;
  }
  .text-right {
    text-align: right;
  }
</style>

<main>
  <Logo title="Sign up" subtitle="Create your Pluoro account" />

  <div class="form">
    <div class="row-two">
      <div class="input-row">
        <Input
          id="firstName"
          on:change={(e) => {
            firstName = e.target.value;
          }}
          value={firstName}
          label="First name" />
      </div>
      <div class="input-row">
        <Input
          id="lastName"
          on:change={(e) => {
            lastName = e.target.value;
          }}
          value={lastName}
          label="Last name" />
      </div>
    </div>
    <div>
      <Input
        id="email"
        on:change={(e) => {
          email = e.target.value;
        }}
        value={email}
        label="Your e-mail address" />
    </div>
    <Small title="You'll need to confirm that this email belongs to you." />
    <div class="row-two">
      <div class="input-row">
        <Input
          id="password"
          on:change={(e) => {
            password = e.target.value;
          }}
          type="password"
          value={password}
          label="Password" />
      </div>
      <div class="input-row">
        <Input
          id="confirmPassword"
          on:change={(e) => {
            confirmPassword = e.target.value;
          }}
          type="password"
          value={confirmPassword}
          label="Confirm" />
      </div>
    </div>
    <Small
      title=" Use 8 or more characters with a mix of letters, numbers and
      symbols" />
    <div class="row-two">
      <div>
        <Link href="/account/sign-in" title="Sign in instead" />
      </div>
      <div class="text-right">
        <Button title="Sign up" on:click={handleSubmit} />
      </div>
    </div>
  </div>

</main>
