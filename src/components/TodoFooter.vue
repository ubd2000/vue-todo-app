<template>
    <!--<button v-on:click="clearTodoItems">모두 삭제</button>-->
    <button v-on:click="$emit('clear')">모두 삭제</button>
</template>

<script>
    export default {
        methods: {
            clearTodoItems: function () {
                this.$emit('clear');
            }
        },
    }
</script>

<style scoped>

</style>

