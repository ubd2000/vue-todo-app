<template>
    <div>
        <!--{{ todoItems }}-->
        <ul>
            <li v-for="(todoItem, index) in propsdata" v-bind:key="index">
                {{ todoItem }}
                <button v-on:click="removeItem(todoItem, index)">
                    remove
                </button>
            </li>
        </ul>
    </div>
</template>

<script>
    export default {
        props: ['propsdata'],
        methods: {
            /**
             *
             * @param todoItem 할일내용
             * @param index 번호
             */
            removeItem: function (todoItem, index) {
                this.$emit('remove', todoItem, index);
            },
        },
    }
</script>

<style>

</style>