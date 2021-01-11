<template>
  <nav @click="navSlide">
    <ul class="nav-links">
      <li><NuxtLink to="/">Home</NuxtLink></li>
      <li><NuxtLink to="/about">About</NuxtLink></li>
      <li><NuxtLink to="/work">Work</NuxtLink></li>
      <li><NuxtLink to="/projects">Projects</NuxtLink></li>
    </ul>
    <div class="burger">
      <div class="line1"></div>
      <div class="line2"></div>
      <div class="line3"></div>
    </div>
  </nav>
</template>

<script>
  export default {
    methods: {
      navSlide: () => {
        const burger = document.querySelector('.burger');
        const nav = document.querySelector('.nav-links');
        const navLinks = document.querySelectorAll('.nav-links li')

        burger.addEventListener('click', () => {
          // Toggle Nav
          nav.classList.toggle('nav-active');

          // Animate links
          navLinks.forEach( (links, index) => {
            if(links.style.animation) {
              links.style.animation = '';
            } else {
              links.style.animation = `navLinkFade .5s ease forwards ${index / 7 + .3}s`;
            }
          });

          // Burger animation
          burger.classList.toggle('toggle');
        });
      }
    }
  }
</script>

<style scoped>
  nav {
    display: flex;
    font-family: 'Poppins', sans-serif;
    justify-content: space-around;
    align-items: center;
    background-color: #5D4954;
    min-height: 8vh;
    overflow-x: hidden;
  }
  .nav-links {
    display: flex;
    justify-content: space-around;
    width: 30%;
    overflow-x: hidden;
  }

  .nav-links li {
    list-style: none;
  }

  .nav-links a {
    color: rgb(219, 219, 219);
    text-decoration: none;
    letter-spacing: 3px;
    font-weight: bold;
    font-size: 14px;
  }
  .burger {
    display: none;
  }

  .burger div{
    width: 25px;
    height: 3px;
    background-color: rgb(219, 219, 219);
    margin: 5px;
    transition: all 0.3s ease;
  }

  @media screen and (max-width: 1024px) {
    /* Increase space between nav elements */
    .nav-links {
      width: 40%;
    }
  }

  @media screen and (max-width: 768px) {
    body {
      overflow-x: hidden;
    }
    /* Nav for mobile */
    .nav-links {
      position: absolute;
      right: 0px;
      height: 92vh;
      top: 8vh;
      background-color: #5D4954;
      flex-direction: column;
      align-items: center;
      width: 40%;
      transform: translateX(100%);
      transition: transform 0.5s ease-in;
    }
    .nav-links li {
      opacity: 0;
    }
    .burger {
      display: block;
      cursor: pointer;
    }
  }

  /* Classes deactivated by default */
  .nav-active {
    transform: translateX(0%);
  }

  @keyframes navLinkFade {
    from {
      opacity: 0;
    }
    to {
      opacity: 1;
      transform: translateX(0px);
    }
  }
</style>
