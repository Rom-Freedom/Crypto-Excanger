<template>
    <div className="input-div">
        <input className="input-field" min="0" type="number" @input="changeAmount($event.target.value)" placeholder="Enter a number">
        <button className="convert-button" @click="convert()">Convert</button>
    </div>
</template>

<script>
    export default {
        props: {
            changeAmount: {
                type: Function,
                required: true
            },
            convert: {
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

.input-div {
    display: flex;
    justify-content: center;
    align-items: center;
    position: relative;
    margin-bottom: 50px;
}
.convert-button {
    color: #fff;
    cursor: pointer;
    background: #1a032d;
    border: 0;
    border-radius: 3px;
    text-transform: uppercase;
    position: absolute;
    top: 30px;
    margin: 0 auto;
    padding: 15px 20px;
    width: 150px;
}
</style>
