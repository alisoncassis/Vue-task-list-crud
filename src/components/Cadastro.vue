<template>
    <div>
        <form @submit.prevent="save()">
            <div class="form-group">
                <label for="description" class="col-sm-2 col-form-label label-input">New Task:</label>
                <div class="input-group">
                    <input type="text" class="form-control" id="description" placeholder="Task description" v-on:keyup="sendInput()">
                    <span class="input-group-btn">
                        <button class="btn btn-secondary" type="submit">Add</button>
                    </span>
                </div>
            </div>
        </form>
    </div>
</template>

<script>

export default {
    props: ['newTask'],

    methods: {
        save() {
            this.$emit('save')
        },
        sendInput() {
            this.$emit('newTask', 'fdsffs')
        }
    },

}

</script>
<style scoped>
.label-input {
    line-height: 2.5
}
</style>
