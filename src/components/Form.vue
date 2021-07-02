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
    mounted() {
        if(localStorage.getItem('value')) {
            try {
                this.listValue = JSON.parse(localStorage.getItem('value'))
            } catch {
                localStorage.removeItem('value')
            }            
        }
    },
    methods: {
        getValue: function() {
            this.listValue.push({
                'title': this.value, 
                'checked': false});
                
            this.value = ''
            this.saveValue();
        },
        saveValue() {
            const parse = JSON.stringify(this.listValue);
            localStorage.setItem('value', parse)
        }
    },
}
</script>
