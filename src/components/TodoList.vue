<template>
    <ol>
        <li v-for="item in listValue" v-bind:key="item.name">
            {{ item.name }}
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