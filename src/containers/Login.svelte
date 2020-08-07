<script>
  import Logo from "../components/Logo.svelte";
  import { setCookie } from "../utils/cookie";
  import Button from "../components/Button.svelte";
  import Input from "../components/Input.svelte";
  import Link from "../components/Link.svelte";
  import { onMount } from "svelte";
  import request, { makeApiUrl, makePostReq } from "../utils/request";
  import Small from "../components/Small.svelte";

  let email = "";
  let password = "";
  let errors = {};
  let generalError = "";
  function redirectToHome() {
    window.location.href = "/";
  }
  const handleSubmit = async () => {
    if (generalError) {
      generalError = "";
    }
    const fields = { email, password };
    Object.keys(fields).forEach((key) => {
      if (!fields[key] || (fields[key] && !fields[key].trim())) {
        errors[key] = "This field is required";
      } else {
        delete errors[key];
      }
    });
    if (Object.keys(errors).length === 0) {
      try {
        const res = await request(
          makeApiUrl(`/account/login`),
          makePostReq(fields)
        );
      } catch (error) {
        errors = {};
        generalError = error;
      }
    }
  };
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
    grid-column-gap: 20px;
  }
</style>

<main>
  <Logo title="Sign in" subtitle="Use your Pluoro account" />

  <div class="form">
    <div>
      <Input
        id="email"
        on:change={(e) => {
          email = e.target.value;
        }}
        value={email}
        label="E-mail"
        error={errors['email']} />
    </div>
    <div class="input-row">
      <Input
        id="password"
        type="password"
        on:change={(e) => {
          password = e.target.value;
        }}
        value={password}
        label="Password"
        error={errors['password']} />
    </div>
    <Small title={generalError} type="error" />
    <div class="row-two">
      <div>
        <Link href="/account/sign-up" title="Create account" />
      </div>
      <div class="text-right">
        <Button title="Sign in" on:click={handleSubmit} />
      </div>
    </div>
  </div>
</main>
