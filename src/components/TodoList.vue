<template>
    <ol>
        <li 
            v-for="(item, index) of listValue" 
            v-bind:key="item.id" 
            v-bind:class="{'done': item.checked}">

            <label>
                <input 
                    type="checkbox" 
                    name="checkbox" 
                    v-model="item.checked">

                {{ item.title }}
            </label>

            <button v-on:click="remove(index)">Удалить</button>
        </li>
    </ol>
</template>

<script>
export default {
    props: {
        listValue: {
            type: Array,
            required: true
        }
    },
    methods: {
        remove(index) {
            this.listValue.splice(index, 1);
            localStorage.setItem('value', JSON.stringify(this.listValue))
        }
    }
}
</script>

<style scoped>
    .done {
        text-decoration: line-through;
    }
</style>