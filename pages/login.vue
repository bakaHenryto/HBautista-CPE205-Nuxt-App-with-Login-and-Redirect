<template>
	<div class="container">
	  <h1>Login</h1>
	  <form @submit.prevent="login">
		<label for="Email">E-mail</label>
		<input type="text" id="Email" name="Email" v-model="email" required>
  
		<label for="password">Password</label>
		<input type="password" id="Password" name="Password" v-model="password" required>
  
		<button class = "btnlogin" @click = 'handleSubmit' type="submit">Log in</button>
	  </form>
	</div>
  </template>
  
<script>

import Cookies from 'js-cookie'

  export default {
	data() {
	  return {
		email: '',
		password: '',
	  };
	},
  
	methods: {
	 async handleSubmit() {
		// Handle login logic here
  
		console.log('Email:', this.email, 'Password:', this.password);
		try {
        const url = 'http://localhost:5000/api/auth/login';
        const response = await fetch(url , {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json',
          },
          body: JSON.stringify({
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
          this.$router.push('/index1');

        } else {
          console.error('Login failed:', data);
        }
      } catch (error) {
        console.error('Login failed:', error.message);
      }
	  },
	},
  };



</script>
  
  <style scoped>
  .container {
	background-color: #fff;
	border-radius: 10px;
	box-shadow: 0px 0px 10px #888888;
	margin: 100px auto;
	max-width: 300px;
	padding: 20px;
  }
  
  h1 {
	color: #333;
	text-align: center;
  }
  
  label {
	display: block;
	margin-bottom: 10px;
  }
  
  input[type="text"],
  input[type="password"] {
	border-radius: 5px;
	border: none;
	box-shadow: 0px 0px 5px #888888;
	margin-bottom: 20px;
	padding: 10px;
	width: 94%;
  }
  
  .btnlogin {
	background-color: #6A5E4E;
	border: none;
	border-radius: 5px;
	color: #fff;
	cursor: pointer;
	font-size: 16px;
	padding: 10px;
	width: 100%;

  }
  
  .btnlogin:hover {
	background-color: #6a5e4e8b;
  }

   

  </style>