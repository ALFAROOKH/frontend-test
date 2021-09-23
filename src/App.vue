<template>
  <div class="container mx-20 flex pt-6 space-x-20">
    <h1 class="text-6xl text-purple-900 font-bold mr-20">Front End Games</h1>
    <div class="pt-6 font-medium space-x-10 text-purple-900">
      <router-link to="/">Home</router-link>
      <router-link to="/">About</router-link>
      <router-link to="/">Games</router-link>
      <router-link to="/">Discover</router-link>
      <router-link to="/">Global Rank</router-link>
      <button class="p-2 bg-purple-900 rounded-full text-purple-200">
        Sign In
      </button>
      <!-- <router-link to="/">Sign in</router-link> -->
    </div>
  </div>
  <router-view />
</template>

<style>
#app {
  background-color: rgb(203, 202, 255);
}
</style>
