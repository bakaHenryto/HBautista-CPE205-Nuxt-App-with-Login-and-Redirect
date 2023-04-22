<template>
    <div class = "container">
        <form class="signup-form" @submit.prevent="handleSubmit">
    
        <label for="username">Username:</label>
        <input id="username" type="text" v-model="username" required>
    
        <label for="email">Email:</label>
        <input id="email" type="email" v-model="email" required>
    
        <label for="password">Password:</label>
        <input id="password" type="password" v-model="password" required>
    
        <button class = "btnsignup" type="Signup">Sign Up</button>
        </form>
    </div>
</template>
  
<script>

import Cookies from 'js-cookie'

  export default {
	data() {
	  return {
        username:'',
		email: '',
		password: '',
	  };
	},
  
	methods: {
	 async handleSubmit() {
		// Handle login logic here
  
		console.log('Email:', this.email, 'Password:', this.password);
		try {
        const url = 'http://localhost:5000/api/auth/signup';
        const response = await fetch(url , {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json',
          },
          body: JSON.stringify({
            username: this.username,
            email: this.email,
            password: this.password,
          }),
        });
        const data = await response.json();
        if (response.ok) {
          console.log('Login successful:', data);

          // Save the response to cookies
          Cookies.set('auth_token', 'your-auth-token');

          // Clear the input fields
          this.email = '';
          this.password = '';

          // Redirect to the dashboard
          this.$router.push('/login');

        } else {
          console.error('Sign up failed:', data);
        }
      } catch (error) {
        console.error('Sign up failed:', error.message);
      }
	  },
	},
  };
</script>
  
  <style>
  .signup-form {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  
  .container {
	background-color: #fff;
	border-radius: 10px;
	box-shadow: 0px 0px 10px #888888;
	margin: 100px auto;
	max-width: 300px;
	padding: 20px;
  }

  label {
    margin-top: 10px;
  }
  
  input {
    margin-bottom: 20px;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 4px;
    width: 300px;
  }
  
  .btnsignup {
    padding: 10px;
    background-color: #6A5E4E;
    color: #fff;
    border: none;
    border-radius: 4px;
    width: 300px;
    cursor: pointer;
  }
  
  .btnsignup:hover {
    background-color: #6a5e4e8b;
  }
  </style>
  