<scrpt setup></scrpt>

<template>
  <div
    class="bg-slate-200 block border rounded-sm p-2 mx-2 border-gray-500 min-w-[300px]"
  >
    <!-- column -->
    <div class="block overflow-hidden text-ellipsis w-4/5 text-lg">標題</div>
    <!-- <textarea class="resize-none overflow-hidden border-none w-full p-1 h-8 block"></textarea> -->

    <!-- tasks -->
    <div
      class="block my-2 w-full py-2 px-3 bg-white overflow-hidden select-none"
    >
      <div class="block font-bold">卡片標題</div>
      <div class="overflow-hidden text-ellipsis">卡片內容</div>
    </div>

    <div
      class="block my-2 w-full py-2 px-3 bg-white overflow-hidden select-none"
    >
      <div class="block font-bold">卡片標題</div>
      <div class="overflow-hidden text-ellipsis">卡片內容</div>
    </div>
    <!-- tasks -->

    <!-- add new task -->
    <AddNewTask />
    <!-- add new task -->
  </div>
</template>
