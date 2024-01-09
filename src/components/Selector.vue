<template>
    <ul class="list-currencies">
        <li class="currency-name">Bitcoin</li>
        <li class="currency-name" >ETH</li>
        <li class="currency-name" >USDT</li>
    </ul>
</template>

<script>
    export default {

    }
</script>

<style scoped>
.list-currencies {
    list-style: none;
    width: 200px;
    padding: 0;
    border-radius: 3px;
    border: 3px solid #000;
}

.currency-name {
    display: block;
    background: #1a032d;
    color: #fff;
    padding: 20px 0px;
}
.currency-name:hover, li.active {
    background: #24043e;
    cursor: pointer;
}
</style>
