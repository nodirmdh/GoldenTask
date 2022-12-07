<script>
import { ref } from 'vue';
export default {
    emits: {
        addTask({ title, description }) {
            if (title === '' || description === '') {
                alert('Заполните поля ввода')
                return false
            }
            return true
        }
    },
    setup(props, { emit }) {
        const title = ref('')
        const description = ref('')

        const addTask = () => {
            emit('addTask', { title: title.value, description: description.value })
            
           title.value = ''
           description.value = ''
                
            
        }
        return {
            title,
            description,
            addTask
        }
    }
}
</script>

<template>
    <form class="card" @submit.prevent="addTask">
        <input type="text" placeholder="Title" v-model="title">
        <input type="text" placeholder="Description" v-model="description">
        <button class="btn add">Add Task</button>
    </form>

</template>

<style>
.card {

    margin: 10px auto;
    background: var(--vt-c-white);
    display: flex;
    align-items: center;
    width: 450px;
    justify-content: space-between;
    padding: 10px;
    border-radius: 12px;
    flex-wrap: wrap;
}

input {
    width: 100%;
    padding: 6px;
    margin-bottom: 5px;
}

.btn {
    width: 100%;


}

.add {
    background: var(--vt-c-black-mute);
    color: #fff;
}

.add:hover {
    background: var(--vt-c-text-light-1);
    border: 2px solid var(--vt-c-indigo);
}
</style>