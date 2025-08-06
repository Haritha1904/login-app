<!-- <script>
    let email = '';
    let password = '';
    let error = '';
    let loading = false;

  
    function handlelogin(event) {
      event.preventDefault();
      error = '';
  
      if (!isValidEmail(email)) {
        error = 'Please enter a valid email address.';
        return;
      }
  
      if (password.length < 6) {
        error = 'Password must be at least 6 characters.';
        return;
      }
  
      loading = true;
  
      setTimeout(() => {
        loading = false;
        alert(` Login successful for ${email}`);
      }, 1500);
    }
  
    function isValidEmail(email) {
      return /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email);
    }
  </script>
  
  <style>
    body {
      margin: 0;
      padding: 0;
      font-family: sans-serif;
      background-color: #f2f2f2;
    }
  
    .login-container {
      max-width: 300px;
      margin: 0 auto;
      padding: 2rem;
      background-color: rgb(238, 238, 237);
      border-radius: 8px;
      text-align: center;
      box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
    }
  
    .logo {
      width: 100px;
      height: auto;
      margin-bottom: 1rem;
    }
  
    h2 {
      margin-bottom: 1.5rem;
    }
  
    input {
      width: 90%;
      padding: 12px;
      margin-bottom: 1rem;
      border: 1px solid #ccc;
      border-radius: 6px;
      font-size: 1rem;
    }
  
    button {
      width: 90%;
      padding: 12px;
      background-color: orangered;
      color: white;
      font-size: 1rem;
      border: none;
      border-radius: 6px;
      cursor: pointer;
    }
  
    button:disabled {
      background-color: #ffa07a;
    }
  
    .error {
      color: red;
      font-size: 0.9rem;
    margin-top: 1rem;
  }
</style>

<div class="login-container">
  <img
    src="https://keccables.ifactory.ai/assets/images/solidRsLogo.png"
    alt="Logo"
    class="logo"
  />
  <h2>Login</h2>
  <form on:submit={handlelogin}>
    <p>Mail</p>
    <input
      type="email"
      placeholder="Type your Email here"
      bind:value={email}
      required
    />
    <p>Password</p>
    <input
      type="password"
      placeholder="Enter your Password"
      bind:value={password}
      required
    />
    <button type="submit" disabled={loading}>
      {loading ? 'Logging in...' : 'Login'}
    </button>
    {#if error}
      <p class="error">{error}</p>
    {/if}
  </form>
</div>
   -->












<script>
    import { onMount } from 'svelte';
    import { goto } from '$app/navigation';
  
    onMount(() => {
      goto('/login');
    
    });
</script>
  