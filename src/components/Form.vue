<template>
    <form>
        <input type="text" v-model="value" placeholder="Введите текст">
        <input type="button" v-on:click.prevent="currentValue" value="Click">
        <p>Сообщение: {{ value }}</p>
    </form>
</template>

<script>
export default {
    data: function() {
        return {
            value: ''
        }
    },
    methods: {
        currentValue: function(event) {
            if(this.value === this.value) {
                event.target.value
            }
        }
    }
}
</script>