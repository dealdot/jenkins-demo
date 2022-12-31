<script setup lang="ts">
defineProps(["modelValue"]);
defineEmits(["update:modelValue"]);



// 学习一下范型
const getArray = <T>(value: T, items: number = 5): T[] =>{
  return new Array(items).fill(value);
};
function getArray1<T>(value: T, items: number = 5): T[] {
 return new Array(items).fill(value);
}
const arr = getArray1<number>(33, 3);
console.log(arr);

//范型约束
interface LengthInterface {
  length: number
}
//要求传入的类型要有length属性
const getArray2 = <T extends LengthInterface>(value: T, items: number = 5): T[] =>{
  return new Array(items).fill(value);
};
const arrx = getArray2<string>('33', 3);
console.log(arrx);

//范型约束中使用类型参数

const myTs = <T extends {length:number}>(obj: T, num: number): T => {
  if(obj.length >= num) {
    return obj
  }else{
    obj.length = num
    return obj
    // const res = {length: num}
    // return res;
  }
}

//连接两个数组
const mergeArray = <T>(arr1: T[], arr2: T[]): T[] =>{
  return arr1.concat(arr2)
}
//传入类型不一致会报错,要在调用的时候指定参数类型
mergeArray<number|string>([1,233],['1','3'])


</script>
<template>
  <h1>This is an child page</h1>
  <input
    :value="modelValue"
    @input="$emit('update:modelValue', $event.target.value)"
  />
</template>

<style>
@media (min-width: 1024px) {
  .child {
    color: red;
  }
}
</style>
