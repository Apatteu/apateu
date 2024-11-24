<script>
    let username = '';
    let email = '';
    let password = '';
    let confirmPassword = '';
    let agreeTerms = false;
    let role = '';
    let passwordError = ''; // Variable to store password mismatch error

    function handleSubmit() {
      if (password !== confirmPassword) {
        passwordError = "Passwords do not match";
      } else {
        passwordError = '';
        // Proceed with form submission (for now, just logging the data)
        console.log({ role, username, email, password, confirmPassword, agreeTerms });
      }
    }

    function closeForm() {
      // Logic for closing the form (for now just resetting the form fields)
      username = '';
      email = '';
      password = '';
      confirmPassword = '';
      agreeTerms = false;
      role = '';
      passwordError = '';
    }
</script>

<style>
  /* Reset margin and padding for the body and html to remove unwanted space */
  :global(html, body) {
    margin: 0;
    padding: 0;
    height: 100%;
  }

  .create-account {
    text-align: center;
    padding: 0.6rem;
    border-radius: 12px;
    background: rgba(255, 255, 255, 0.8);
    box-shadow: 0px 4px 12px rgba(0, 0, 0, 0.1);
    width: 410px;
    max-width: 100%;
    margin: 0 auto;
    /* Explicitly remove margin-top */
    margin-top: 0;
    /* Ensure no padding is adding space around the container */
    padding-top: 0;
  }

  .create-account h2 {
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

  .form-group input,
  .form-group select {
    width: 100%;
    padding: 0.5rem;
    border: 1px solid #ccc;
    border-radius: 6px;
    font-size: 0.85rem;
    outline: none;
  }

  .form-group input:focus,
  .form-group select:focus {
    border-color: #ff6a00;
  }

  .checkbox-container {
    display: flex;
    align-items: center;
    font-size: 0.8rem;
    color: #555;
    margin-top: 0.4rem;
    text-align: left;
    width: 80%;
    max-width: 240px;
    margin: 0.4rem auto;
    gap: 10px;
  }

  .checkbox-container input[type="checkbox"] {
    margin-right: 0.3rem;
  }

  .checkbox-container label {
    font-size: 0.8rem;
    color: #555;
    margin: 0;
  }

  .checkbox-container a {
    color: #ff6a00;
    text-decoration: none;
  }

  .checkbox-container a:hover {
    text-decoration: underline;
  }

  .create-account .button-container {
    display: flex;
    justify-content: space-between; /* Push the buttons to opposite sides */
    width: 80%;
    max-width: 240px;
    margin-top: 1rem;
  }

  .close-button {
    background-color: #ccc;
    width: 110px; /* Set the width of the Close button */
    padding: 0.5rem;
    border: none;
    border-radius: 6px;
    color: white;
    font-size: 0.85rem;
    cursor: pointer;
    text-align: center;
    text-decoration: none; /* Remove underline */
  }

  .close-button:hover {
    background-color: #999;
  }

  .submit-button {
    background-color: #ff6a00;
    width: 110px; /* Set the width of the Create button */
    padding: 0.5rem;
    border: none;
    border-radius: 6px;
    color: white;
    font-size: 0.85rem;
    cursor: pointer;
    margin-left: auto; /* Move the Create button to the far right */
  }

  .submit-button:hover {
    background-color: #e65b00;
  }

  .error-message {
    color: #ff6a00;
    font-size: 0.85rem;
    margin-top: 0.5rem;
  }

  /* Responsive Styling */
  @media (max-width: 768px) {
    .create-account {
      width: 90%; /* Increase width on smaller screens */
      margin-top: 0; /* Ensure no margin-top on small screens */
    }

    .form-group {
      width: 100%; /* Allow the input fields to use the full width on smaller screens */
    }

    .checkbox-container {
      width: 100%; /* Allow the checkbox container to span the full width */
    }

    .create-account h2 {
      font-size: 1.1rem; /* Make the heading smaller on mobile */
    }

    .submit-button,
    .close-button {
      width: 100%; /* Make buttons full width on smaller screens */
      margin: 0.5rem 0;
    }
  }

  @media (max-width: 480px) {
    .create-account {
      width: 95%; /* Increase width for extremely small screens */
    }

    .submit-button,
    .close-button {
      width: 100%; /* Full width buttons */
      padding: 0.7rem;
    }
  }
</style>

<div class="create-account">
  <h2>Create Your Account</h2>
  <form on:submit|preventDefault={handleSubmit}>
    <div class="form-group">
      <label for="role">Role</label>
      <select id="role" bind:value={role} required>
        <option value="" disabled selected>Select your role</option>
        <option value="Tenant">Tenant</option>
        <option value="Landlord">Landlord</option>
      </select>
    </div>

    <div class="form-group">
      <label for="username">Username</label>
      <input
        id="username"
        type="text"
        placeholder="Enter your username"
        bind:value={username}
        required
      />
    </div>

    <div class="form-group">
      <label for="email">Email Address</label>
      <input
        id="email"
        type="email"
        placeholder="example@gmail.com"
        bind:value={email}
        required
      />
    </div>

    <div class="form-group">
      <label for="password">Password</label>
      <input
        id="password"
        type="password"
        placeholder="**********"
        bind:value={password}
        required
      />
    </div>

    <div class="form-group">
      <label for="confirmPassword">Confirm Password</label>
      <input
        id="confirmPassword"
        type="password"
        placeholder="**********"
        bind:value={confirmPassword}
        required
      />
    </div>

    {#if passwordError}
      <div class="error-message">{passwordError}</div>
    {/if}

    <div class="checkbox-container">
      <input
        id="agreeTerms"
        type="checkbox"
        bind:checked={agreeTerms}
        required
      />
      <label for="agreeTerms">
        I agree with <a href="/terms">Terms and Conditions</a> and <a href="/privacy">Privacy Policy</a>.
      </label>
    </div>

    <!-- Buttons: Close on left, Submit on right -->
    <div class="button-container">
      <!-- Close button with href (navigates to a different page) -->
      <a href="/" class="close-button">Close</a>
      <button type="submit" class="submit-button">Create</button>
    </div>
  </form>
</div>
