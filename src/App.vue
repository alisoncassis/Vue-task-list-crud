<template>
    <div class="container text-center">
        <h1>{{ msg }}</h1>
        <div class="">
            <form @submit.prevent="addTask">
                <div class="form-group">
                    <label for="description" class="col-sm-2 col-form-label label-input mt-10">New Task:</label>
                    <div class="input-group">
                        <input autofocus type="text" class="form-control" id="description" placeholder="Task description" v-model="newTask">
                        <span class="input-group-btn">
                            <button class="btn btn-secondary" type="submit">Add</button>
                        </span>
                    </div>
                </div>
            </form>
        </div>
        <div class="tasks" v-for="task of previousTasks">
            <task :description="task" @clickEvent="removeTask(task)"/>
        </div>
    </div>
</template>

<script>
import Task from './components/Task.vue'

export default {
    components: {
        'task': Task
    },

    data () {
        return {
            msg: 'Welcome to Your Tasks App',
            tasks: [],
            newTask: ""
        }
    },

    methods: {
        removeTask(task) {
            this.tasks.splice(this.tasks.indexOf(task), 1);
            localStorage.setItem('tasks', JSON.stringify(this.tasks))
        },
        addTask() {
            this.tasks.push(this.newTask)
            localStorage.setItem('tasks', JSON.stringify(this.tasks))
            this.newTask = ""
        }
    },

    computed: {
        previousTasks() {
            this.tasks = JSON.parse(localStorage.getItem('tasks') || '[]');
            return this.tasks
        }
    }
}

</script>

<style>

.container {
    margin-top: 50px;
}
.mt-10 {
    margin-top: 10px;
}
.tasks {
    background: rgba(236, 236, 236, 0.93);
    padding: 0 15px;
    border-radius: 30px;
}

</style>
