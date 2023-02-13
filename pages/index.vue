<template>
  <div class="link-container">
    <NuxtLink to="/days/day1">Day1</NuxtLink>
    <NuxtLink to="/days/day2">Day2</NuxtLink>
    <NuxtLink to="/days/day3">Day3</NuxtLink>
    <NuxtLink to="/days/day4">Day4</NuxtLink>
    <NuxtLink to="/days/day5">Day5(未投稿)</NuxtLink>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  name: 'IndexPage',
})
</script>

<style lang="scss">
.link-container {
  display: flex;
  flex-direction: column;
}
</style>
