<template>
    <ul>
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
    </ul>
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
    ul {
        display: flex;
        flex-direction: column;
        width: 290px;
        max-height: 700px;
        overflow-y: auto;
        border-radius: 10px;
        list-style: none;
        background-color: rgb(128, 128, 128);
    }
    ul {
      scrollbar-width: thin;
      scrollbar-color: rgb(128, 128, 128) rgb(128, 128, 128);
    }
    ul::-webkit-scrollbar {
        width: 12px;               
    }
    ul::-webkit-scrollbar-track {
        background: rgb(128, 128, 128);      
    }
    ul::-webkit-scrollbar-thumb {
        background-color: rgb(128, 128, 128);   
        border-radius: 10px;      
        border: 1px solid rgb(128, 128, 128);  
    }
    ::v-deep li {
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        padding: 10px;
    }

</style>