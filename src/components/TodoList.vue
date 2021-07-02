<template>
    <ol>
        <li v-for="item in listValue" v-bind:key="item.id" v-bind:class="{'done': item.checked}">
            <label>
                <input type="checkbox" name="checkbox" v-model="item.checked">
                {{ item.title }}
            </label>
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
    }
}
</script>

<style scoped>
    .done {
        text-decoration: line-through;
    }
</style>