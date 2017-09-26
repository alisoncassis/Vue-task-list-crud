<template>
    <div class="container text-center">
        <h1>{{ msg }}</h1>
        <task-input v-on:save="grava()" v-on:newTask="novaTask()"/>
        <div class="tarefas" v-for="task of tasks">
            <task :description="task.description" v-on:clickEvent="remove(description)"/>
        </div>
    </div>
</template>

<script>
import Input from './components/Cadastro.vue'
import Task from './components/Task.vue'

export default {
    components: {
        'task-input': Input,
        'task': Task
    },

    data () {
        return {
            msg: 'Welcome to Your Tasks Crud App',
            tasks: [],
            newTask: ""
        }
    },

    methods: {
        remove(description) {
            console.log('oi')
            if (localStorage != undefined) {
                this.tasks = this.tasks.filter(task => {
                    return task.description != description
                })
                localStorage.setItem('tasks', JSON.stringify(this.tasks))
            }
        },
        grava() {
            if (localStorage != undefined) {
                this.tasks.push(this.newTask)
                localStorage.setItem('tasks', JSON.stringify(this.tasks))
            }
        },
        prepareLocalStorage() {
            if(localStorage.getItem('tasks') == null) {
                localStorage.setItem('tasks', '[]')
            }
            this.tasks = JSON.parse(localStorage.getItem('tasks'));
        },
        novaTask(text) {
            console.log(text)
        }
    },

    computed: {

    },

    created() {
        this.prepareLocalStorage()
        // if (localStorage != undefined) {
        //     const previousTasks = JSON.parse(localStorage.getItem('tasks'))
        //     previousTasks.length > 0 ? this.tasks = previousTasks : this.tasks = ""
        // }
        // this.tasks = JSON.parse(localStorage.getItem('tasks') || '[]');
    }
}

</script>

<style>

.container {
    margin-top: 50px;
}

</style>
