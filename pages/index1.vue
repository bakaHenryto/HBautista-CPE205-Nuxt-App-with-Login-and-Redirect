<template>
    <!-- Navbar start -->
    <nav class="navbar">
          <!-- Logo start -->
          <div class="navtitle">
        <img src="../public/tablogo.png" alt="img" class = "navlogo" >
              <p class="navtitle1">HIVEMED</p>
          </div>
          <!-- Logo end -->
  
          <!-- Toggler start -->
      <div class = "navcontent">
        <button @click = 'landingpage' role="menubar" class="md">
          <i class="btn1"></i>
            <a href="" class="btn" role="menuitem" >
              Log out
            </a>
        </button>
  
      </div>
          <!-- Toggler end -->
      </nav>
    <!-- Navbar end -->
    
    <!-- Main section start -->
      <section class="main-section">
          <div class="main-section1">
              <!-- Main text start -->
              <h1 class="maintitlecontext ">
                  
                  HIVEMED 
              </h1>
              <p class="maincontext">
                  Welcome to the future of healthcare, where social media and medicine come together to empower you.
              </p>
              <!-- Main text end -->
  
              <!-- Social links start -->
              <div class="flex mt-3 gap-8">
                  
              </div>
              <!-- Social links end -->
          </div>
  
          <!-- image start -->
          <div class="main-sectionimg">
              <img src="../public/MainLogo.png" alt="img" class="h-full">
          </div>
          <!-- image end -->
  
      </section>
    <!-- Main section end -->
  </template>
  
<script>
import Cookies from 'js-cookie'
  export default {
      methods: {
         landingpage(){
            this.$router.push('/');
            Cookies.remove('auth_token') 
            this.authToken = ''
         }
      }
  }
</script>
  
  <style>
  .navbar {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    width: 90%;
    padding: 1rem;
    padding-left: 5rem;
    padding-right: 5rem;
    background-color: rgba(255, 255, 255, 0.9);
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.2);
    display: flex;
    justify-content: space-between;
    align-items: center;
    z-index: 50;
  }
  
  .navtitle {
    height: 100%;
    display: flex;
    flex-direction: row;
    justify-content: flex-start;
    margin-top: 0rem;
    margin-bottom: 0rem;
  }
  
  .navcontent {
    position: absolute;
    left: 0;
    right: 0;
    transform: translateY(16px);
    background-color: rgba(255, 255, 255, 0.9);
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.2);
    display: none;
    flex-direction: column;
    gap: 0.5rem;
    align-items: center;
    padding: 0.5rem;
  }
  
  @media (min-width: 768px) {
    .navcontent {
      background-color: none;
      box-shadow: none;
      display: flex;
      flex-direction: row;
      position: static;
      transform: none;
    }
  }
  
  .md {
    display: none;
    padding-top: 5px;
    padding-right: 5px;
    padding-bottom: 5px;
    padding-left: 5px;
    width: 7rem;
  }

  .md:hover{
    background-color: #6a5e4e8b;
  }
  
  @media (min-width: 768px) {
    .md {
      display: block;
    }
  }
  
  .navtitle1 {
    letter-spacing: 0.1em;
    font-weight: bold;
    padding-top: 0rem;
    padding-left: 1rem;
    font-family: 'Montserrat';
  }
  
  .btn{
    font-family: 'Montserrat';
    font-size: 15px;
    color: #f5f5f4;
    text-decoration: none;
  }
  
  .main-section {
    height: 100vh;
    padding-left: 12px;
    padding-right: 12px;
    padding-top: 8px;
    padding-bottom: 32px;
    margin-bottom: 8px;
    margin-left: 7rem;
  }
  
  @media (min-width: 1024px) {
    .main-section {
      padding-left: 32px;
      padding-right: 32px;
    }
  }
  
  .main-section1 {
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
  }
  
  @media (min-width: 768px) {
    .main-section1 {
      width: 50%;
    }
  }
  
  .main-sectionimg {
    position: absolute;
    bottom: 0;
    right: 0;
    overflow: hidden;
    height: 0rem;
    z-index: -50;
    margin-right: 5rem;
  
  }
  
  .h-full{
    height: 25rem;
  }
  
  @media (min-width: 640px) {
    .main-sectionimg {
      height: 50%;
    }
  }
  
  @media (min-width: 768px) {
    .main-sectionimg {
      height: 60%;
    }
  }
  
  @media (min-width: 1024px) {
    .main-sectionimg {
      height: 66.666666%;
    }
  }
  
  .maincontext {
    text-transform: none ;
  }
  
  @media (min-width: 1280px) {
    .maincontext {
      width: 50%;
    }
  }
  
  .maincontext {
    color: #6b7280;
  }
  
  .maintitlecontext {
    text-transform: uppercase;
    font-size: 4rem;
    margin-bottom: 1rem;
    font-weight: 600;
  }
  
  @media (min-width: 1280px) {
    .maintitlecontext {
      font-size: 3rem;
    }
  }
  
  .navlogo{
    height: 3rem;
    padding-top: 0rem;
    padding-left: 1rem;
  }
  
  </style>