<script setup>
import { RouterLink, RouterView } from 'vue-router'
import Nav from '@/components/Navbar.vue'
import Title from '@/components/Title.vue'
import Location from '@/components/Location.vue'
</script>

<template>
  <header>
    <Title />
    <Nav />
  </header>
  <main>
    <RouterView />
  </main>
  <Location />
</template>

<style>
@import '@/assets/base.css';

#app{
  width: 100%;
  height: 100%;
  display: flex;
}
header{
  width: 50%;
  height: 100%;
  padding: 10rem;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
main{
  width: 50%;
  height: 100%;
  padding-inline: 10rem;
  display: flex;
  align-items: center;
}

@media screen and (orientation: portrait) {
  #app{
    flex-direction: column;
  }
  header{
    position: absolute;
    top: 0;
    left: 0;
    padding: 0;
    width: 100%;
    height: 100%;
    justify-content: space-between;
    align-items: flex-start;
    pointer-events: none;
  }
  main{
    width: 100%;
    height: calc(100% - 10rem);
    margin-top: 5rem;
  }
}
</style>
