<script setup lang="ts">
import { ref, onMounted } from 'vue';



    const todos = ref<any>(null);


    async function fetchData() {
        try {
            const response = await fetch('https://jsonplaceholder.typicode.com/todos');
            const data = await response.json();
            todos.value = data;
        }catch (error) {
            console.log(error)
        }
    }

    onMounted(() => {
        fetchData()
    })


</script>

<template>
    <div>
       <ul>
        <li v-for="todo in todos" :key="todo.id">
            <div>{{ todo.title }}</div>
        </li>
       </ul>
    </div>

</template>