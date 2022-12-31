<template>
  <main>
    <TheWelcome />
  </main>
</template>

<script setup lang="ts">
import TheWelcome from "../components/TheWelcome.vue";
import { ref, reactive, watch, watchEffect, watchPostEffect } from "vue";
const num = ref(0);
const state = reactive({ name: "zong", count: 22 });
const state1 = reactive({
  message: {
    id: 7,
    attrs: {
      name: "liu",
      count: 19,
    },
  },
});
// setTimeout(() => {
//   num.value++;
// }, 4000);

//监听num值
// watch(num, (newVal: number, oldVal: number) => {
//   console.log("新: ", newVal, "旧", oldVal);
// });
// setTimeout(() => {
//   state.count++;
// }, 1000);

// setTimeout(() => {
//   state1.message.attrs.count++;
// }, 1000);

// setInterval(() => {
//   state1.message.attrs.count++;
// }, 1000);

//监听reactive()对象
// watch(
//   () => state.count,
//   (newVal: number, oldVal: number) => {
//     console.log("新: ", newVal, "旧", oldVal);
//   }
// );
//监听多个数据
// watch([() => state.count, num], ([newCount, newNum], [oldCount, oldNum]) => {
//   console.log("新count", newCount, "老count", oldCount);
//   console.log("新num", newNum, "老num", oldNum);
// });
//监听复杂的对象属性,这里如果监听state1.message则newType和oldType都是修改后的message对象
//因为指针没有变，只是修改指针所指向的内存的值
// const stopwatch = watch(
//   () => state1.message,
//   (newType, oldType) => {
//     console.log("new: ", newType.attrs.count, "old: ", oldType.attrs.count);
//   },
//   { deep: true }
// );
//watch可以返回一个函数，调用后可移除监听
//一般组件卸载的时候就会自动停止watch监听，但如果没有跟组件进行绑定则不会自动卸载，需要手动卸载
// setTimeout(() => {
//   stopwatch();
// }, 10000);
setTimeout(() => {
  state.count++;
  //num.value++;
}, 3000);
//watchEffect不需要传递依赖，会在组件初始化时执行一次收集依赖
//然后当依赖中的数据发生变化时，再次执行回调函数
watchEffect(
  () => {
    console.log(state.count);
    console.log(num.value);
  },
  //flush: post 确保dom是更新后的状态
  {
    flush: "post",
  }
);
//如果想获取更新后的状态，可以使用vue3的,
watchPostEffect(() => {
  //确保dom是更改后的状态
});
</script>
