<template>
  <div class="about">
    <h1>This is an about page</h1>
    <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Eos veritatis quisquam, odit ratione quas ea consequatur cum
      nostrum inventore sint perspiciatis dolorum voluptatibus fugiat exercitationem illum facilis blanditiis facere. Eaque?
    </p>
    <nav>
      <router-link to="/">Home</router-link>
    </nav>
  </div>
</template>

<style scoped>
nav {
  padding: 10px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}
nav a.router-link-exact-active {
  color: #42b983;
}
</style>
