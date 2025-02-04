<script setup>
import { ref } from "vue";
import { useFocus } from "@vueuse/core";
import { vOnClickOutside } from "@vueuse/components";
import { useStore } from "/src/stores";

// 處理使用者游標焦點
const target = ref();
useFocus(target, { initialValue: true });

// 切換狀態
const isEditing = ref(false);
const title = ref("");

const store = useStore();
const { addNewCard } = store;

const addCard = () => {
  addNewCard(title.value);
  title.value = "";
  isEditing.value = false;
};
</script>
<template>
  <div class="new-card">
    <div @click="isEditing = true" v-if="!isEditing" class="block select-none">
      + 新增其他列表
    </div>
    <div v-else>
      <input
        type="text"
        ref="target"
        class="w-full p-2 block"
        placeholder="為列表輸入標題"
        v-on-click-outside="() => (isEditing = false)"
        v-model="title"
        @keydown.enter="addCard"
      />
    </div>
  </div>
</template>

<style scoped>
.new-card {
  @apply border rounded-sm cursor-pointer bg-slate-200 bg-opacity-70 border-gray-500 
    mx-2 min-w-[300px] p-2 w-[300px] block hover:bg-opacity-90;
}
</style>
