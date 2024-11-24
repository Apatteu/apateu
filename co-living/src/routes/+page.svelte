<script>
    let email = '';
    let password = '';
    let passwordError = ''; // To handle any error messaging
  
    function handleSubmit() {
      if (!email || !password) {
        passwordError = "Both fields are required";
      } else {
        passwordError = '';
        // Proceed with form submission (log for now)
        console.log({ email, password });
      }
    }
  </script>
  
  <style>
  /* Resetting margin and padding */
  body, html {
    margin: 0;
    padding: 0;
    height: 100%;
    font-family: Arial, sans-serif;
  }
  
  /* Container for the entire layout */
  .container {
    display: flex;
    justify-content: space-between;
    align-items: flex-end; /* Aligns content at the bottom */
    height: 80vh; /* Full screen height */
    padding: 2rem;
    box-sizing: border-box;
  }
  
  /* Left side content (h2 and p) */
  .left-side {
    width: 45%;
    text-align: left;
    padding-right: 2rem; /* Ensure content is not too close to the form */
    display: flex;
    flex-direction: column;
    justify-content: flex-end; /* Align content at the bottom */
  }
  
  .left-side h2 {
    font-size: 2rem;
    color: #333;
    margin-bottom: 1rem;
  }
  
  .left-side p {
    font-size: 1rem;
    color: #555;
  }
  
  /* The form container positioned on the right */
  .create-account {
    text-align: center;
    padding: 0.6rem;
    border-radius: 12px;
    background: rgba(255, 255, 255, 0.8);
    box-shadow: 0px 4px 12px rgba(0, 0, 0, 0.1);
    width: 400px;
    max-width: 100%;
    margin: 0 auto;
    flex-shrink: 0; /* Prevent shrinking */
  }
  
  /* Add margin-top to h2 inside create-account */
  .create-account h2 {
    margin-top: 2rem; /* Add space at the top of the h2 */
    margin-bottom: 0.8rem;
    color: #333;
    font-size: 1.3rem;
    font-weight: bold;
  }
  
  .form-group {
    display: flex;
    flex-direction: column;
    width: 80%;
    max-width: 240px;
    margin: 0.5rem auto;
    text-align: left;
  }
  
  .form-group label {
    font-size: 0.8rem;
    color: #555;
    margin-bottom: 0.2rem;
    font-weight: 500;
  }
  
  .form-group input {
    width: 100%;
    padding: 0.5rem;
    border: 1px solid #ccc;
    border-radius: 6px;
    font-size: 0.85rem;
    outline: none;
  }
  
  .form-group input:focus {
    border-color: #ff6a00;
  }
  
  .create-account button {
    width: 80%;
    max-width: 240px;
    padding: 0.5rem;
    margin-top: 0.8rem;
    border: none;
    border-radius: 6px;
    background-color: #ff6a00;
    color: white;
    font-size: 0.85rem;
    cursor: pointer;
  }
  
  .create-account button:hover {
    background-color: #e65b00;
  }
  
  .links {
    margin-top: 1rem;
    font-size: 0.85rem;
    color: #666;
  }
  
  .links a {
    color: #ff6a00;
    text-decoration: none;
  }
  
  .links a:hover {
    text-decoration: underline;
  }
  
  .error-message {
    color: #ff6a00;
    font-size: 0.85rem;
    margin-top: 0.5rem;
  }
  </style>
  
  <div class="container">
  <!-- Left side content (without modifying the form container) -->
  <div class="left-side">
    <h2>Apateu</h2>
    <p>Find your ideal co-living space effortlessly. With Apateu, discover shared apartments, manage unit partitions, and connect with the perfect housemates all in one place. Start your journey toward better shared living today!</p>
  </div>
  
  <!-- Right side form (no modification to this container) -->
  <div class="create-account">
    <h2>Login</h2>
    <form on:submit|preventDefault={handleSubmit}>
      <div class="form-group">
        <label for="email">Email Address</label>
        <input
          id="email"
          type="email"
          placeholder="Enter your email"
          bind:value={email}
          required
        />
      </div>
  
      <div class="form-group">
        <label for="password">Password</label>
        <input
          id="password"
          type="password"
          placeholder="Enter your password"
          bind:value={password}
          required
        />
      </div>
  
      {#if passwordError}
        <div class="error-message">{passwordError}</div>
      {/if}
  
      <button type="submit">Login</button>
    </form>
  
    <div class="links">
      <p><a href="/forgot-password">Forgot Password?</a></p>
      <p>
        Don't have an account? <a href="./signin">Register</a>
      </p>
    </div>
  </div>  
  </div>
  