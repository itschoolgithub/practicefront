<template>
    <h2>Калькулятор</h2>
    <input
        type="number"
        v-model="a"
    >
    <input
        type="number"
        v-model="b"
    >
    <button
        @click="sendForm"
    >Отправить</button>
    <h2
        v-if="result !== null"
    >Результат: {{ result }}</h2>
</template>

<script>
    import axios from 'axios';
    export default {
        data() {
            return {
                a: null,
                b: null,
                result: null
            }
        },
        methods: {
            async sendForm() {
                const response = await axios.get(`http://practice.be/calc.php?a=${this.a}&b=${this.b}`)
                this.result = response.data.result;
            }
        }
    }
</script>