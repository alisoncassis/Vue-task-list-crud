<template>
    <div class="mt-25">
        <div class="task row">
            <p class="lead col-xs-8">
                {{description}}
            </p>
            <div class="text-right col-xs-4">
                <button type="button" class="btn btn-danger" @click="clickEvent()">Remove</button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: ['description'],
    methods: {
        clickEvent() {
            this.$emit('clickEvent')
        }
    }
}
</script>

<style lang="css">
.mt-25 {
    margin-top: 25px;
}
.lead {
    margin-top: 10px;
    word-wrap: break-word;
}
.task {
    display: flex;
    align-items: center;
}
.btn-danger {
    padding: 6px 8px;
}
</style>
