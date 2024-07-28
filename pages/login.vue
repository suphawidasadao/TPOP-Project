<template>
  <div class="login-container">
    <div class="top-section"></div>
    <div class="bottom-section">
      <h1>T-POP Hub</h1>
      <form @submit.prevent="login">
        <div class="input-group">
          <i class="fas fa-envelope"></i>
          <input type="email" id="email" v-model="email" placeholder="อีเมล" required />
        </div>
        <div class="input-group">
          <i class="fas fa-lock"></i>
          <input type="password" id="password" v-model="password" placeholder="รหัสผ่าน" required />
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
  background-color: white;
  height: 45%;
}

.bottom-section {
  background: linear-gradient(to bottom, #ff9fdf, #F0569A);
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 65%;
  padding: 1em;
}

h1 {
  font-size: 4em;
  margin-top: 0;
  color: white;
}

form {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
  max-width: 350px; /* Adjust max width to a better balance */
}

.input-group {
  margin-bottom: 1.2em;
  width: 100%;
  display: flex;
  align-items: center;
  position: relative;
}

input {
  padding: 0.8em; /* Adjust padding */
  font-size: 1em; /* Adjust font size */
  border: none;
  border-radius: 0.5em;
  width: 100%;
  box-sizing: border-box;
}

.input-group i {
  position: absolute;
  left: 10px;
  font-size: 1.2em;
  color: #888;
}

.input-group input {
  padding-left: 2.5em; 
}

.login-button, .register-button {
  width: 50%;
  font-size: 1em;
  padding: 0.8em; 
  border-radius: 2em;
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
</style>
