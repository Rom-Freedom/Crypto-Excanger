<template>
    <input className="input-field" min="0" type="number" @input="changeAmount($event.target.value)" placeholder="Enter a number">
</template>

<script>
    export default {
        props: {
            changeAmount: {
                type: Function,
                required: true
            }
        }
    }
</script>

<style scoped>
.input-field {
    outline: none;
    width: 500px;
    position: relative;
    top: -50px;
    border-radius: 3px;
    border: 0;
    padding: 10px 15px;
    background: #fafafa;
    color: #333;
    font-size: 1.2em;
}
</style>
