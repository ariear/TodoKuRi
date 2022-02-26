<template>
        <input type="text" v-model="title" @keyup.enter="addtodo" required placeholder="todo here" class="border bg-[#F5F5F5] font-pupylinux w-[280px] py-2 px-3 ml-[30px] mt-9 rounded-md shadow mb-10">

        <div v-for="todo in todos" :key="todo.id" class="border border-black w-[90%] mx-auto mb-4 py-3 pl-3 rounded-lg shadow transition-all dark:bg-slate-200">
            <p class="font-pupylinux pr-3">{{ todo.title }}</p>
        </div>
</template>

<script>
export default {
    data() {
        return {
            title: '',
            todos: []
        }
    },
    created(){
        if (localStorage.todos) {
            this.todos = JSON.parse(localStorage.getItem('todos'))
        }
    },
    methods: {
        addtodo(){
            this.todos.unshift({ id: this.todos.length , title: this.title })
            localStorage.setItem('todos', JSON.stringify(this.todos))
            this.title = ''
        }
    },
}
</script>
