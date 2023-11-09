<script setup>
import { ref } from "vue";

defineProps({
  msg: String
});

const count = ref(0);
const incrementCount = () => count.value++;
</script>

<template>
  <div>
    <div>{{count}}</div>
    <div @click="incrementCount"  class="bg-indigo-400 text-black h-10 w-15 p-2 rounded-sm mt-5 cursor-pointer">Add</div>
  </div>
</template>


