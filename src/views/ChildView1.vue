<script setup lang="ts">
import { computed } from "vue";
const props = defineProps(["modelValue"]);
const emit = defineEmits(["update:modelValue"]);
//定义一个计算属性
const value = computed({
  get() {
    return props.modelValue;
  },
  set(value) {
    emit("update:modelValue", value);
  },
});
</script>
<template>
  <h1>This is an child page</h1>
  <!-- 在这里使用v-model引用计算属性 -->
  <input v-model="value" />
</template>

<style>
@media (min-width: 1024px) {
  .child {
    color: red;
  }
}
</style>
