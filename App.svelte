<script>
  import schema from "./schema";

  import { createForm } from "svelte-forms-lib";

  const { form, errors, handleChange, handleSubmit, isValid } = createForm({
    initialValues: {
      email: "",
      password: "",
      confirmPassword: "",
      country: "",
      checkbox: ""
    },
    validationSchema: schema,
    onSubmit: values => {
      alert(JSON.stringify(values));
    }
  });
</script>

<div class="container">
  <h1>Registration Form</h1>
  <form on:submit|preventDefault={handleSubmit}>
    <div>
      <input
        type="text"
        name="email"
        bind:value={$form.email}
        placeholder="Email"
        on:change={handleChange}
      />

      {#if $errors.email}
        <span class="error">{$errors.email}</span>
      {/if}
    </div>

    <div>
      <input
        type="password"
        name="password"
        bind:value={$form.password}
        placeholder="Password"
        on:change={handleChange}
      />

      {#if $errors.password}
        <span class="error">{$errors.password}</span>
      {/if}
    </div>
    <div>
      <input
        type="password"
        name="confirmPassword"
        bind:value={$form.confirmPassword}
        placeholder="Confirm password"
        on:change={handleChange}
      />

      {#if $errors.confirmPassword}
        <span class="error">{$errors.confirmPassword}</span>
      {/if}
    </div>

    <div>
      <select name="country" bind:value={$form.country} on:blur={handleChange}>
        <option value="">Select a country</option>
        <option value="England">England</option>
        <option value="USA">USA</option>
        <option value="France">France</option>
      </select>
      {#if $errors.country}
        <span class="error">{$errors.countr}</span>
      {/if}
    </div>

    <div>
      <label for="checkbox">Check this box</label>
      <input
        name="checkbox"
        type="checkbox"
        bind:checked={$form.checkbox}
        on:change={handleChange}
      />
      {#if $errors.checkbox}
        <span class="error">{$errors.checkbox}</span>
      {/if}
    </div>

    <div>
      <button type="submit">Register</button>
    </div>
  </form>
</div>

<style>
  .container {
    margin: 0 auto;
    width: 400px;
  }

  form div {
    margin-top: 1em;
  }

  :root {
    --primary-light: #a6f9d6;
    --primary: #5be2a9;
    --primary-dark: #53ce9a;
    --secondary: #1e2145;
    --white: #fff;
    --grey: #e6e6ff;
    --grey-dark: #6d7098;
    --red: #ff6b6b;
  }

  input,
  select {
    font-family: inherit;
    font-size: inherit;
    max-width: 400px;
    width: 100%;
    padding: 12px;
    box-sizing: border-box;
    border: 1px solid var(--grey);
    border-radius: 4px;
    transition: all 150ms ease;
    background: var(--white);
  }

  input:focus,
  select:focus {
    outline: none;
    box-shadow: 0 0 0 4px rgb(227, 227, 245);
    border-color: var(--grey);
  }

  input:disabled,
  select:disabled {
    color: #ccc;
  }

  button {
    color: #fff;
    background-color: var(--primary);
    border: none;
    text-transform: uppercase;
    letter-spacing: 1.8px;
    outline: none;
    border-radius: 4px;
    display: block;
    margin-top: 12px;
    line-height: 1.8;
    font-size: 12px;
    padding: 10px 18px;
    width: 100%;
    transition: all 150ms ease;
    cursor: pointer;
  }

  button:disabled {
    background-color: var(--grey);
  }

  button:focus:not(:disabled) {
    box-shadow: 0 0 0 4px var(--primary-light);
  }

  button:hover:not(:disabled) {
    background-color: var(--primary-dark);
  }

  .error {
    display: block;
    font-size: 12px;
    color: var(--red);
  }
</style>
