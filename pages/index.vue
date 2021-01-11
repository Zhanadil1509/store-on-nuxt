<template>
  <NuxtLink to="/">Home</NuxtLink>
</template>
<template>
  <main class="container">
    <h1>Home Page</h1>
    <NuxtLink to="/about">About</NuxtLink>
  </main>
</template>


<script>
export default {}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
</style>
