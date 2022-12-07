<script>
import { EMPTY_OBJ } from '@vue/shared';

export default {
    emits: ['onDone', 'onRemove'],
    props: {
        task: {
            required: true,
        }
    },
    setup(props, { emit }) {
        const onDone = () => {
            emit('onDone')
        }

        const onRemove = () => {
            emit('onRemove')
        }

        return {
            onDone,
            onRemove
        }
    }
}
</script>

<template>
    <div class="card">
        <div class="card-header">
            <h1>{{ task.title }}</h1>
            <p>{{ task.description }}</p>
            
        </div>
        <div class="card-btn">
            <button @click="onDone" v-if="!task.status" class="btn done">Done</button>
            <button @click="onRemove" v-else class="btn warning">Delete</button>
        </div>
    </div>
</template>
  
<style scoped>
.card {
    margin: 0 auto;
    background: var(--vt-c-white);
    display: flex;
    align-items: center;
    width: 450px;
    justify-content: space-between;
    padding: 10px;
    border-radius: 12px;
    outline: 2px solid var(--vt-c-indigo);
}

.card-header {
    width: 80%;
    padding-left: 10px;
    position: relative;
}
.card-header h1 {
    font-weight: 600;
    color: var(--vt-c-black);
    font-size: 23px;
    overflow-wrap: anywhere;
}

.card-header p {
    color: var(--vt-c-black-soft);
    overflow-wrap: anywhere;
}

.btn {
    width: 70px;
    
}

.done {
    background: rgb(0, 141, 0);
    color: #fff;
}

.done:hover{
    background: rgb(51, 80, 9);
    
}

.warning {
    background: red;
    color: #fff;
}

.warning:hover{
    background: rgb(129, 2, 2);
}
</style>