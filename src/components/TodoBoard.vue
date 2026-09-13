<script setup>
import { ref } from 'vue'

const inputTodo = ref('')
const todoLists = ref([])
// 次に新規作成するid
let nextId = 1

// 編集中のid
const editingId = ref(null)

// 編集用inputの値
const editingTitle = ref('')

function submitTodo(todo) {
  todoLists.value.unshift({ id: nextId, title: todo })
  nextId += 1
  inputTodo.value = ''
}

function editTodo(id, title) {
  editingId.value = id
  editingTitle.value = title
}

function saveTodo(id, title) {
  const targetIndex = todoLists.value.findIndex((todo) => todo.id === id)
  if (targetIndex !== -1) {
    todoLists.value[targetIndex].title = title
  }
  editingId.value = ref(null)
  editingTitle.value = ref('')
}

function deleteTodo(id) {
  const targetIndex = todoLists.value.findIndex((todo) => todo.id === id)
  if (targetIndex !== -1) {
    todoLists.value.splice(targetIndex, 1)
  }
}
</script>
<template>
  <div class="todo-wrap">
    <div class="card">
      <h2 class="title">TODO追加</h2>
      <label>タイトル</label>
      <input v-model="inputTodo" />
      <button @click="submitTodo(inputTodo)">追加</button>
    </div>
    <div class="card">
      <ul>
        <li v-for="todo in todoLists" :key="todo.id">
          <!-- 通常表示 -->
          <template v-if="todo.id !== editingId">
            ID:{{ todo.id }}　{{ todo.title }}
            <button @click="editTodo(todo.id, todo.title)">編集</button>
            <button @click="deleteTodo(todo.id)">削除</button>
          </template>
          <!-- 編集時 -->
          <template v-else>
            ID:{{ todo.id }}　<input v-model="editingTitle" />
            <button @click="saveTodo(todo.id, editingTitle)">保存</button>
          </template>
        </li>
      </ul>
    </div>
  </div>
</template>
<style scoped>
h2 {
  margin-top: 0;
}
.todo-wrap {
  display: flex;
  justify-content: space-around;
  margin-bottom: 40px;
}
</style>
