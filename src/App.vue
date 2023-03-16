<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
    <div class="wrapper">
      <nav>
        <p>Eworld</p>
        <div>
          <RouterLink to="/">Home</RouterLink>
          <RouterLink to="/repos">Repos</RouterLink>
        </div>
        <div class="social_icons">
          <a href="https://twitter.com/Eworld_Tech" target="_blank"
            ><i class="fa-brands fa-twitter"></i
          ></a>
          <a href="https://github.com/josephe44" target="_blank"
            ><i class="fa-brands fa-github"></i
          ></a>
        </div>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  padding-top: 1rem;
  padding-bottom: 1rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

nav a.router-link-exact-active {
  color: #002147;
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

.social_icons {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 15px;
}

.social_icons a {
  color: #000;
  border: none;
  padding: 0;
}
</style>
