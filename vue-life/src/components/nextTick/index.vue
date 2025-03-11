<template>
  <div>
    <div v-if="showText" ref="textRef" id="text">UFO</div>
    <button @click="getText">点击获取文本</button>
  </div>
</template>
<script setup lang="ts">
import { ref, nextTick } from "vue";
const showText = ref(false);
const textRef = ref<HTMLElement | null>(null);
const getText = async () => {
  showText.value = !showText.value;
  console.log("输出textRef", textRef.value); // 访问更新前的 textRef
  const text = document.querySelector("#text");
  console.log("text", text); // 访问更新前的 text
  await nextTick();

  console.log("输出nextTick下的textRef", textRef.value); // 访问更新后的 textRef
  const text2 = document.querySelector("#text");
  console.log("text2", text2); // 访问更新后的 text
};
</script>
