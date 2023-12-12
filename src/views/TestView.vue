<template>
    <div class="login-container">
      <h2>Login</h2>
      <form @submit.prevent="login">
        <div class="form-group">
          <label for="username">Username:</label>
          <input type="text" id="username" v-model="username" required>
        </div>
        <div class="form-group">
          <label for="password">Password:</label>
          <input type="password" id="password" v-model="password" required>
        </div>
        <button type="submit">Login</button>
      </form>
      <p v-if="loginError" class="error-message">{{ loginError }}</p>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        username: '',
        password: '',
        loginError: ''
      };
    },
    methods: {
      login() {
        // 在这里可以添加登录逻辑，例如检查用户名和密码是否正确
        if (this.username === 'your_username' && this.password === 'your_password') {
          // 登录成功，可以执行跳转或其他操作
          console.log('Login successful');
          // 这里可以使用路由跳转或其他方式处理登录成功的情况
        } else {
          // 登录失败
          this.loginError = 'Invalid username or password';
        }
      }
    }
  };
  </script>
  
  <style>
  .login-container {
    max-width: 300px;
    margin: auto;
    text-align: center;
  }
  
  .form-group {
    margin-bottom: 15px;
  }
  
  input[type="text"],
  input[type="password"],
  button {
    padding: 8px;
    width: 100%;
    box-sizing: border-box;
  }
  
  button {
    background-color: #007bff;
    color: white;
    border: none;
    cursor: pointer;
  }
  
  .error-message {
    color: red;
  }
  </style>
  