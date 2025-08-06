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
    let email = '';
    let password = '';
    let error = '';
    let loading = false;
    let showPassword = false;
  
    function handleLogin(e) {
      e.preventDefault();
      error = '';
      loading = true;
  
      setTimeout(() => {
        loading = false;
        alert(`Login successful for ${email}`);
      }, 1000);
    }
  </script>
  
  <style>
    * {
      box-sizing: border-box;
      padding: 0;
      margin: 0;
    }
  
    .container {
      display: flex;
      height: 100vh;
      font-family: sans-serif;
    }
  
    .left {
      flex: 1;
      background-color: white;
      padding: 3rem 2rem;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
    }
  
    .right {
      flex: 1;
      background-color: #eeeeee;
      display: flex;
      justify-content: center;
      align-items: center;
    }
  
    .login-box {
      width: 100%;
      max-width: 360px;
    }
  
    h2 {
      font-size: 2rem;
      font-weight: bold;
      margin-bottom: 0.5rem;
      color: #000;
      text-align: left;
    }
  
    p.subtitle {
      font-size: 0.95rem;
      color: #777;
      margin-bottom: 2rem;
      text-align: left;
    }
  
    label {
      font-size: 0.9rem;
      font-weight: 500;
      margin-bottom: 0.3rem;
      color: #222;
      display: block;
    }
  
    input {
      width: 100%;
      padding: 0.75rem;
      font-size: 1rem;
      border: 1px solid #ddd;
      border-radius: 6px;
      margin-bottom: 1rem;
    }
  
    .password-wrapper {
      position: relative;
    }
  
    .toggle-visibility {
      position: absolute;
      top: 50%;
      right: 12px;
      transform: translateY(-50%);
      cursor: pointer;
      font-size: 1rem;
    }
  
    button {
      width: 100%;
      padding: 0.75rem;
      background-color: #ff6a00;
      color: white;
      font-size: 1rem;
      border: none;
      border-radius: 6px;
      cursor: pointer;
      transition: background-color 0.2s;
    }
  
    button:hover {
      background-color: #e55d00;
    }
  
    .logo-right {
      width: 100px;
      opacity: 0.7;
    }
  
    .error {
      color: red;
      font-size: 0.9rem;
      margin-top: 1rem;
      text-align: center;
    }
  </style>
  
  <div class="container">
    <div class="left">
      <div class="login-box">
        <h2>Login</h2>
        <p class="subtitle">Enter your email below to login to your account</p>
        <form on:submit={handleLogin}>
          <div>
            <label>Email</label>
            <input type="email" placeholder="Email" bind:value={email} required />
          </div>
  
          <div class="password-wrapper">
            <label>Password</label>
            <input
              type={showPassword ? 'text' : 'password'}
              placeholder="Password"
              bind:value={password}
              required
            />
            <span
              class="toggle-visibility"
              on:click={() => (showPassword = !showPassword)}
              title="Toggle password"
              >👁️</span>
             
          </div>
  
          <button type="submit" disabled={loading}>
            {loading ? 'Logging in...' : 'Login'}
          </button>
  
          {#if error}
            <p class="error">{error}</p>
          {/if}
        </form>
      </div>
    </div>
  
    <div class="right">
      <img
        src="https://keccables.ifactory.ai/assets/images/solidRsLogo.png"
        alt="Logo"
        class="logo-right"
      />
    </div>
</div>
  
