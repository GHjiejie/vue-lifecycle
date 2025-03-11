<template>
  <div>
    <child></child>
    <span ref="countRef">{{ count }}</span>
    <button @click="updateCount">更新count</button>
  </div>
</template>
<script setup lang="ts">
import { ref } from "vue";
import child from "./demo-1/child.vue";
import { onBeforeUpdate, onUpdated } from "vue";
const count = ref(0);
const countRef = ref<HTMLElement | null>(null);

const updateCount = () => {
  count.value++;
};

onBeforeUpdate(() => {
  console.log("输出beforeUpdate下的count", count.value);
  console.log("输出更新之前的count", countRef.value?.textContent);
});

onUpdated(() => {
  console.log("输出updated下的count", count.value);
  console.log("输出更新之后的count", countRef.value?.textContent);
});
</script>
