<template>
    <div class="todo-list">
        <div v-if="todos && todos.length > 0">
            <todoItem 
                v-for="todo in todos"
                :key="todo._id"
                :_id="todo._id"
                :title="todo.title"
                :description="todo['description']" />
        </div>
        <div v-else class="no-todos">
            No todos :( create one
        </div>
    </div>
</template>

<script>
import todoItem from '@/components/todoItem'
export default {
    components: {
        todoItem
    },
    props: {
        todos: {
            required: true,
            type: Array
        }
    }
}
</script>

<style lang="scss" scoped>
    .todo-list {
        flex: 1;
    }

    .no-todos {
        padding: 20px;
        font-size: 23px;
        font-weight: bold;
        text-align: center;
    }
</style>