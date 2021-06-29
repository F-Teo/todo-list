<template>
    <form @submit.prevent="getValue">
        <input type="text" v-model="value" placeholder="Введите текст">
        <input type="submit" value="Click">
        <p>Сообщение: {{ currentValue }}</p>
    </form>
</template>

<script>
export default {
    data: function() {
        return {
            value: '',
            currentValue: ''
        }
    },
    methods: {
        getValue: function() {
            this.currentValue = this.value;
            this.value = ''
        },
    }
}
</script>
