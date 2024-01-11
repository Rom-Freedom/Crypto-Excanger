<template>
    <h2>Options in favorites</h2>
    <div @click="getFromFavs(index)" className="outputFav" v-for="(el, index) in favs" :key="index">
        <span className="outCurrency" id="curr-1">{{ el.from }}</span>
        <span className="outCurrency" id="curr-1">{{ el.to }}</span>
    </div>
</template>
  
<script>
  export default {
    props: {
        favs: {
            type: Array,
            required: true
        },
        getFromFavs: {
            type: Function,
            required: true
        }
    }
}    
</script>
  
  
<style scoped>
h2 {
    color: #fff;
} 
.outputFav {
    display: flex;
    justify-content: space-between;
    width: 500px;
    margin: 0 auto;
    transition: all .5s ease;
    
}

.outCurrency {
    padding: 10px 15px;
    background: #8c00ff;
    color: #fff;
}
#curr-1 {
    margin-bottom: 15px;
}
.outputFav:hover {
    opacity: 0.7;
    transform: scale(1.03);
}
</style>
  