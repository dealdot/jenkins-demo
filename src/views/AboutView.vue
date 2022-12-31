<script setup lang="ts">
import ChildView from "@/views/ChildView.vue";
import { ref } from "vue";
const searchText = ref("hello");
</script>
<template>
  <div class="about">
    <ChildView v-model="searchText"></ChildView>
    <h1>This is an about page {{ searchText }}</h1>
    <!-- <ChildView
      :modelValue="searchText"
      @update:modelValue="(newValue) => (searchText = newValue)"
    ></ChildView> -->
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
