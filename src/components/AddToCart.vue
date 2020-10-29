<template>
  <button class="addToCart btn py-2" v-on:click="order" >
      Add to Cart
  </button>
</template>

<script>
export default {
name:'AddToCart',
methods: {
    order : function(){
        this.$emit('order', "hey")
    }
}
}
</script>

<style lang="scss" scoped>
*{
    font-family: DM Sans;
    font-style: normal;
    font-weight: bold;
}
.addToCart{
    font-size: 22px;
    line-height: 29px;
    padding: 16px;
    color: #fff;
    background: #32C574;
    box-shadow: 0px 0px 10px rgba(50, 197, 116, 0.59);
    border-radius: 8px;
    width:90vw;
    &:hover{
        color:#ffffff;
        background: #32C574;
    };
    &:focus{
        background: #32C574B5;
        box-shadow: 0 0 0 0.2rem rgb(210, 255, 212);
    }
}
</style>