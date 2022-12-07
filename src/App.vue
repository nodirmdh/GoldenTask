<script>
import AppInput from './components/AppInput.vue';
import AppCard from './components/AppCard.vue';
import { ref } from 'vue';

export default{
  setup(){
    const taskList = ref([
      {id: 1, title: 'Первая задача', description: 'Сделать первую задачу', status: false},
    ])

    const addTask = ({title, description}) => {
      taskList.value = [...taskList.value,{id: taskList.value.length + 1, title, description, status: false}]
    }

    const doneTask = (id) => {
      taskList.value = taskList.value.map(i => {
        if(i.id === id) 
          i.status = true
        return i
      })
    }

    const removeTask = (id) => {
      taskList.value = taskList.value.filter(i => i.id !== id)
    }

    return{
      taskList,
      addTask,
      doneTask,
      removeTask
    }
  },
  components: {AppCard,AppInput}
}
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />

  </header>
  <main>
    <ul class="list">
      <li class="item" v-for="item in taskList" :key="item.id">
        <app-card :task="item" @onDone="doneTask(item.id)" @onRemove="removeTask(item.id)"></app-card>
      </li>
    </ul>
    <app-input @addTask="addTask"></app-input>
  </main>


</template>

<style scoped>

.logo {
  display: block;
  margin: 0 auto 2rem;
}
.list{
  padding: 0;
}
.item{
  list-style: none;
  margin: 10px 0 0 0;
}
</style>
