<script setup lang="ts">
interface Item {
  content: string
  checked: boolean
  idx: number
}

const todoList: Item[] = reactive([
  {
    content: 'todo1',
    checked: false,
    idx: 0,
  },
  {
    content: 'todo2',
    checked: false,
    idx: 1,
  },
  {
    content: 'todo3',
    checked: false,
    idx: 2,
  },
])

function handleRemove(idx: number) {
  todoList.splice(idx, 1)
}

const InputContent = ref('')
function handleInput() {
  todoList.push({
    content: InputContent.value,
    checked: false,
    idx: todoList.length,
  })
  console.log('test')
}
</script>

<template>
  <div flex flex-wrap flex-col items-center justify-center>
    <h2 text-3xl pb-4>
      TodoList
    </h2>

    <div border rounded-md shadow-xl class="w-[350px]">
      <input
        v-model="InputContent" type="text" border-b w-full outline-none px-4 py-1
        placeholder="Add Your daily Work 🥱"
        @keydown.enter="handleInput"
      >
      <div
        v-for="item in todoList" :key="item.idx"
        border-b
      >
        <div class="flex justify-between items-center" px-4 py-1>
          <div class="flex items-center ">
            <input type="checkbox" :checked="item.checked">
            <span class="ml-2" :class="{ 'line-through': item.checked }">
              {{ item.content }}
            </span>
          </div>
          <button class="text-red-500" @click="handleRemove(item.idx)">
            <img src="https://api.iconify.design/system-uicons:cross.svg" alt="">
          </button>
        </div>
      </div>
    </div>
  </div>
</template>
