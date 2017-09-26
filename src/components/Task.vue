<template>
    <div class=" mt-50">
        <div class="task">
            <p class="lead col-xs-8">
                {{description}}
            </p>
            <div class="text-right col-xs-4">
                <button type="button" class="btn btn-default" @click="clickEvent()">Remove</button>
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
.mt-50 {
    margin-top: 50px;
}
.lead {
    margin-top: 10px;
}
</style>
