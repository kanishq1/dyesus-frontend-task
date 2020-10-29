<template>
      <select class="form-control form-control-lg quantity-selector mx-auto mb-4"  @change="update($event)">
      <option v-for="index in qty" :key="index" :value="index">Qty : {{index}}</option>
      </select>
</template>

<script>
export default {
    name:'QuantitySelector',
    data: ()=>{
      return {
        qty :5
      }
    },
    methods:{
      update : function(event){
        this.$emit("updateQty", event.target.value);
      }
    }
}
</script>

<style lang="scss">
*{
    font-family: DM Sans;
    font-style: normal;
    font-weight: bold;
}
.quantity-selector{
  height: 60px;
  width: 90vw;
  font-size: 16px;
  font-weight: bold;
  background-color: #F2F3F5;
border: 1px solid rgba(0, 0, 0, 0.25);
box-sizing: border-box;
border-radius: 8px;
&:focus{
  border: 1px solid rgba(0, 0, 0, 0.25);
  box-shadow: none;
}
}
input[type='radio']:checked {
   background: #32C574;
}
</style>