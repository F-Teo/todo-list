<template>
    <div>
        <form @submit.prevent="getValue">
        <input type="text" v-model="value" placeholder="Введите текст">
        <input type="submit" value="Click">
    </form>

    <TodoList v-bind:listValue="listValue" />
    </div>
</template>

<script>
import TodoList from './TodoList.vue'

export default {
    components: {
        TodoList
    },
    data: function() {
        return {
            value: '',
            listValue: []
        }
    },
    methods: {
        getValue: function() {
            this.listValue.push({'title': this.value, 'id': ''})
            this.value = ''
        },
    }
}
</script>
