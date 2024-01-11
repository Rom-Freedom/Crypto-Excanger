<template>
    <ul className="list-currencies">
        <li className="currency-name" @click="setCrypto('BTC')" :className="cryptoNow == 'BTC' ? 'active' : ''">Bitcoin</li>
        <li className="currency-name" @click="setCrypto('ETH')" :className="cryptoNow == 'ETH' ? 'active' : ''">ETH</li>
        <li className="currency-name" @click="setCrypto('USDT')" :className="cryptoNow == 'USDT' ? 'active' : ''">USDT</li>
    </ul>
</template>

<script>
    export default {
        props: {
            setCrypto: {
                type: Function,
                required: true
            },
            cryptoNow: {
                type: String,
                required: true
            }
        },
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
