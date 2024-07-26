<template>
    <div class="login-container">
      <div class="top-section">
        <h1>T-POP Hub</h1>
      </div>
      <div class="bottom-section">
        <form @submit.prevent="login">
          <div class="input-group">
            <label for="email">
              <i class="fas fa-envelope"></i>
              <input type="email" id="email" v-model="email" placeholder="อีเมล" required />
            </label>
          </div>
          <div class="input-group">
            <label for="password">
              <i class="fas fa-lock"></i>
              <input type="password" id="password" v-model="password" placeholder="รหัสผ่าน" required />
            </label>
          </div>
          <button type="submit" class="login-button">ล็อคอิน</button>
          <button type="button" class="register-button" @click="goToRegister">สร้างบัญชี</button>
        </form>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        email: '',
        password: ''
      };
    },
    methods: {
      async login() {
        try {
          const response = await fetch('https://api.example.com/login', {
            method: 'POST',
            headers: {
              'Content-Type': 'application/json'
            },
            body: JSON.stringify({
              email: this.email,
              password: this.password
            })
          });
          const data = await response.json();
          if (response.ok) {
            // Handle successful login (e.g., store token, redirect)
            console.log('Login successful:', data);
          } else {
            // Handle login error
            console.error('Login error:', data.message);
          }
        } catch (error) {
          console.error('Error during login:', error);
        }
      },
      goToRegister() {
        // Navigate to the register page
        this.$router.push('/register');
      }
    }
  };
  </script>
  
  <style scoped>
  .login-container {
    display: flex;
    flex-direction: column;
    height: 100vh;
  }
  
  .top-section {
    flex: 1;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: white;
  }
  
  .bottom-section {
    flex: 1;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    background: linear-gradient(to bottom, #ff9fdf, #ff9fdf);
    padding: 1em;
  }
  
  h1 {
    font-size: 3em;
    margin: 0;
    color: #ff9fdf;
  }
  
  form {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100%;
    max-width: 400px;
  }
  
  .input-group {
    margin-bottom: 1.5em;
    width: 100%;
  }
  
  input {
    padding: 1em;
    font-size: 1.2em;
    border: none;
    border-radius: 0.5em;
    width: 100%;
  }
  
  .login-button, .register-button {
    width: 100%;
    font-size: 1.2em;
    padding: 1em;
    border-radius: 0.5em;
    cursor: pointer;
    margin-bottom: 1em;
  }
  
  .login-button {
    background-color: #007bff;
    color: white;
    border: none;
  }
  
  .register-button {
    background-color: white;
    color: #007bff;
    border: 1px solid #007bff;
  }
  
  button:hover {
    opacity: 0.9;
  }
  
  i {
    margin-right: 0.5em;
  }
  </style>
  