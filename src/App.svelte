<script>
  import { Route } from "tinro";
  import { getCookie } from "./utils/cookie";
  import NotFound from "./containers/NotFound.svelte";
  import Home from "./containers/Home/Home.svelte";
  import Login from "./containers/Login.svelte";
  import Register from "./containers/Register.svelte";

  const isLoggedIn = !!getCookie("TestAuthorization");

  if (isLoggedIn) {
    window.location.href = "/";
  }

  const base = "/account";

  let theme = localStorage.getItem("theme") || "light";
  const onThemeChange = () => {
    const newTheme = theme === "light" ? "dark" : "light";
    localStorage.setItem("theme", newTheme);
    theme = newTheme;
  };
</script>

<style>
  .base {
    margin: 0 8%;
  }
  @media only screen and (max-width: 1024px) {
    .base {
      margin: 0 10px;
    }
  }
  :global(a.active) {
    color: var(--primary) !important;
  }
  :global(*) {
    margin: 0px;
    padding: 0px;
    font-family: sans-serif;
  }
  :global(html),
  :global(body) {
    height: 100%;
  }
  :global(#root) {
    min-height: 100%;
    background-color: var(--background);
  }
  :global(.theme-light) {
    --primary: #d21e2b;
    --text: #333;
    --background: #fff;
    --edge: #f6f6f6;
    --neutral: #9c9999;
  }
  :global(.theme-dark) {
    --primary: #d21e2b;
    --text: #fff;
    --background: #0e0e0e;
    --edge: #444;
    --neutral: #383636;
  }
</style>

<div id="root" class="theme-{theme}">
  {#if !isLoggedIn}
    <div class="base">
      <Route>
        <Route path={base} redirect="{base}/sign-in">
          <Login />
        </Route>
        <Route path="{base}/sign-in">
          <Login />
        </Route>
        <Route path="{base}/sign-up">
          <Register />
        </Route>
        <Route fallback>
          <NotFound />
        </Route>
      </Route>
    </div>
  {/if}
</div>
