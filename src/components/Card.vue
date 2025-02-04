<script setup>
import { ref, computed, watch } from "vue";
import { useStore } from "/src/stores";
import { useFocus } from "@vueuse/core";
import { vOnClickOutside } from "@vueuse/components";

const props = defineProps({
  id: String,
  title: String,
  tasks: Array,
});

// 注意，不可直接修改 props 的值
const title = ref(props.title);
const isTitleEditing = ref(false);

const store = useStore();
const { updateListTitle } = store;

const target = ref();
useFocus(target, { initialValue: true });

watch(isTitleEditing, (v) => {
  updateListTitle(props.id, title.value);
});
</script>

<template>
  <div
    class="bg-slate-200 block border rounded-sm p-2 mx-2 border-gray-500 min-w-[300px]"
  >
    <!-- column -->
    <div
      v-if="!isTitleEditing"
      @click="isTitleEditing = true"
      class="block overflow-hidden text-ellipsis w-4/5 text-lg"
    >
      {{ title }}
    </div>
    <textarea
      v-else
      ref="target"
      v-model="title"
      @keydown.enter="isTitleEditing = false"
      v-on-click-outside="() => (isTitleEditing = false)"
      class="resize-none overflow-hidden border-none w-full p-1 h-8 block"
    >
    </textarea>

    <!-- tasks -->

    <!-- tasks -->
    <TaskItem />
    <!-- add new task -->
    <AddNewTask />
    <!-- add new task -->
  </div>
</template>
