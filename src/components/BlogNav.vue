<template>
  <nav>
    <h1 class="nav_title">
      <router-link to="/">{{ content.title }}</router-link>
    </h1>
    <transition-group tag="menu" name="">
      <li v-for="label in labels" class="nav__item" :key="label" @click="navBack">
        <i class="nav__item--icon"></i>
        <span class="nav__item--label">{{ label }}</span>
      </li>
    </transition-group>
  </nav>
</template>


<script>
  export default {
    name: 'blog-nav'
  }
</script>


<style scoped>

</style>
