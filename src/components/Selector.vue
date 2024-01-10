<template>
    <ul className="list-currencies">
        <li className="currency-name" @click="selectItem('BTC')" :className="current == 'BTC' ? 'active' : ''">Bitcoin</li>
        <li className="currency-name" @click="selectItem('ETH')" :className="current == 'ETH' ? 'active' : ''">ETH</li>
        <li className="currency-name" @click="selectItem('USDT')" :className="current == 'USDT' ? 'active' : ''">USDT</li>
    </ul>
</template>

<script>
    export default {
        props: {
            setCrypto: {
                type: Function,
                required: true
            }
        },
        data() {
            return {
                current: ''
            }
        },
        methods: {
           selectItem(val) {
            this.setCrypto(val);
            this.current = val;
           } 
        }
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
