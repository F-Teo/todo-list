<template>
    <div class="wrapper container">
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
                'Oops, error'
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
            let parse = JSON.stringify(this.listValue);
            localStorage.setItem('value', parse)
        }
    },
}
</script>


<style scoped>
    .wrapper {
        max-width: 320px;
        margin: 0 auto;
    }
    .container {
        display: flex;
        flex-direction: column;
        align-items: center;
        margin-top: 100px;
        padding: 10px;
        border: 1px solid black;
        border-radius: 10px;
        background-color: rgb(128, 128, 128);
    }
    ::v-deep input[type=text] {
        width: 225px;
        border-radius: 5px;
        border: none;
        outline: none;
        padding: 8px 0 8px 5px;
        margin-bottom: 20px;
        margin-right: 10px;
    }
    ::v-deep input[type=submit] {
        border: none;
        border-radius: 3px;
        padding: 8px;
        background-color: lawngreen;
        color: black;
    }
    ::v-deep input[type=submit]:hover {
        background-color: khaki;
    }
</style>