<template>
  <div class="container">
    <div class="form">
      <h1>T-POP Hub</h1>
      <form @submit.prevent="register">
        <div class="input-group">
          <i class="fas fa-user"></i>
          <input
            type="text"
            v-model="username"
            placeholder="ชื่อผู้ใช้"
            required
          />
          <span class="divider"></span>
        </div>
        <div class="input-group">
          <i class="fas fa-user"></i>
          <input
            type="text"
            v-model="fullname"
            placeholder="ชื่อ-สกุล"
            required
          />
          <span class="divider"></span>
        </div>
        <div class="input-group">
          <i class="fas fa-envelope"></i>
          <input type="email" v-model="email" placeholder="อีเมล" required />
          <span class="divider"></span>
        </div>
        <div class="input-group">
          <i class="fas fa-lock"></i>
          <input
            type="password"
            v-model="password"
            placeholder="รหัสผ่าน"
            required
          />
          <span class="divider"></span>
        </div>
        <div class="input-group">
          <i class="fas fa-lock"></i>
          <input
            type="password"
            v-model="confirmPassword"
            placeholder="รหัสผ่านอีกครั้ง"
            required
          />
          <span class="divider"></span>
        </div>
        <div class="button-group">
          <button type="submit" class="register-button">สร้างบัญชี</button>
          <button type="button" class="login-button" @click="login">
            ล็อคอิน
          </button>
        </div>
      </form>
    </div>
  </div>
</template>
     
    <script>
export default {
  data() {
    return {
      username: "",
      fullname: "",
      email: "",
      password: "",
      confirmPassword: "",
    };
  },
  methods: {
    register() {
      // Add your registration logic here
      console.log(
        "Register",
        this.username,
        this.fullname,
        this.email,
        this.password,
        this.confirmPassword
      );
    },
    login() {
      // Add your login logic here
      console.log("Login");
    },
  },
};
</script>
     
    <style scoped>
@import url("https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.min.css");

.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background: linear-gradient(to bottom, #ff9fdf, #F0569A);
}

.form {
  text-align: center;
  width: 500px;
}

h1 {
  color: white;
  margin-bottom: 2rem;
  font-size: 4em;
}

.input-group {
  position: relative;
  margin-bottom: 1rem;
}

.input-group i {
  position: absolute;
  left: 10px;
  top: 50%;
  transform: translateY(-50%);
  color: #999;
}

.input-group input {
  width: 100%;
  padding: 0.75rem 0.75rem 0.75rem 2.5rem;
  margin-top: 0.5rem;
  border: none;
  border-radius: 15px;
  box-sizing: border-box;
}

.input-group .divider {
  position: absolute;
  height: 40px;
  left: 30px;
  top: 8px;
  bottom: 15px;
  width: 1px;
  background-color: #ccc;
}

.button-group {
  display: flex;
  justify-content: space-between;
  margin-top: 2rem;
}

.register-button,
.login-button {
  width: 48%;
  padding: 0.75rem;
  border: none;
  border-radius: 20px;
  color: white;
  cursor: pointer;
}

.register-button {
  background-color: #007bff;
}

.login-button {
  background-color: #6c757d;
}
</style>