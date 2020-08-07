<script>
  import Logo from "../components/Logo.svelte";
  import { setCookie } from "../utils/cookie";
  import Button from "../components/Button.svelte";
  import Input from "../components/Input.svelte";
  import Link from "../components/Link.svelte";
  import Small from "../components/Small.svelte";
  import request, { makePostReq, makeApiUrl } from "../utils/request";
  let firstName = "";
  let lastName = "";
  let email = "";
  let password = "";
  let confirmPassword = "";
  let errors = {};
  let generalError = "";
  function redirectToHome() {
    window.location.href = "/";
  }
  function validateEmail(email) {
    const re = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
    return re.test(String(email).toLowerCase());
  }
  async function handleSubmit() {
    if (generalError) {
      generalError = "";
    }
    const fields = { firstName, lastName, email, password, confirmPassword };
    Object.keys(fields).forEach((key) => {
      if (!fields[key] || (fields[key] && !fields[key].trim())) {
        errors[key] = "This field is required";
      } else {
        delete errors[key];
      }
    });
    if (!errors["password"]) {
      if (password !== confirmPassword) {
        errors["password"] = "Passwords have to be the same";
      } else {
        delete errors.password;
      }
    }
    if (!errors["email"]) {
      if (!validateEmail(email)) {
        errors["email"] = "Please enter valid format of E-mail";
      } else {
        delete errors.email;
      }
    }
    if (Object.keys(errors).length === 0) {
      try {
        delete fields.confirmPassword;
        const res = await request(
          makeApiUrl(`/account/register`),
          makePostReq(fields)
        );
      } catch (error) {
        errors = {};
        generalError = error;
      }
    }
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
    grid-column-gap: 20px;
    align-items: baseline;
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
          label="First name"
          error={errors['firstName']} />
      </div>
      <div class="input-row">
        <Input
          id="lastName"
          on:change={(e) => {
            lastName = e.target.value;
          }}
          value={lastName}
          label="Last name"
          error={errors['lastName']} />
      </div>
    </div>
    <div>
      <Input
        id="email"
        on:change={(e) => {
          email = e.target.value;
        }}
        value={email}
        label="Your e-mail address"
        error={errors['email']} />
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
          label="Password"
          error={errors['password']} />
      </div>
      <div class="input-row">
        <Input
          id="confirmPassword"
          on:change={(e) => {
            confirmPassword = e.target.value;
          }}
          type="password"
          value={confirmPassword}
          label="Confirm"
          error={errors['confirmPassword']} />
      </div>
    </div>
    <Small
      title=" Use 8 or more characters with a mix of letters, numbers and
      symbols" />
    <Small title={generalError} type="error" />
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
