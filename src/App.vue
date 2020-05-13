<template>
    <div>
        <p>{{ msg }}</p>
        <main v-if="show">메인</main>
        <todo-header></todo-header>
        <todo-input v-on:add="inputItem"></todo-input>
        <todo-list v-bind:propsdata="todoItems" v-on:remove="removeItem"></todo-list>
        <todo-footer v-on:clear="clearItems"></todo-footer>
    </div>
</template>
<script>
    import TodoHeader from './components/TodoHeader.vue'
    import TodoInput from './components/TodoInput.vue';
    import TodoList from './components/TodoList.vue';
    import TodoFooter from './components/TodoFooter.vue';

    export default{
        components : {
            'todo-header': TodoHeader,
            'todo-input': TodoInput,
            'todo-list': TodoList,
            'todo-footer': TodoFooter
        },
        data() {
            return {
                todoItems: [],
                show: true
            }
        },
        methods: {
            fetchTodoItems: function () {
                for (var i = 0; i < localStorage.length; i++) {
                    var value = localStorage.key(i);
                    this.todoItems.push(value);
                }
            },
            clearItems: function () {
                this.todoItems = [];
                localStorage.clear();
            },
            inputItem: function (text) {
                localStorage.setItem(text, text);
                this.todoItems.push(text);
            },
            removeItem: function (todoItem, index) {
                // 배열 변경
                this.todoItems.splice(index, 1);
                // 브라우저 저장소(DB)에서 삭제
                localStorage.removeItem(todoItem)
            }
        },
        created: function () {
            this.fetchTodoItems();
        }
    }
</script>

<style>
</style>
