<template>
<div class="variant-selector">
    <div class="form-check variant mx-auto my-2" v-for="(i,k) in variants" :key="k" :class="{ active: k === active}">
        
        <label class="form-check-label" :for='k'>
        <input class="form-check-input" type="radio" name="exampleRadios" :id="k" :value="i.label" v-on:click="changeVariant(i.id)">
           {{i.label}}
        <div class="row mx-0">
            <p v-if="i.listprice" class="list-price col-6 p-0">{{i.listprice}}</p>
            <p v-if="i.discount" class="discount col-6">{{i.discount}}</p>
        </div>
         </label>
    </div>
</div>
</template>

<script>
export default {
    name:'VariantSelector',
    data: () => {
        return {
            variants: [{id:0, label:' 30 Gummies - $ 10'},{id:1,label:'90 Gummies - $ 20', listprice:"List Price: USD 30", discount:'Save $30'},{id:2,label:'Monthly subscription',  discount:'Save 20%'}],
            active: null
        }
    },
    methods: {
        changeVariant : function(i){
           this.active = i
        }
    }
}
</script>

<style lang="scss">
.variant-selector{
    margin-top: 20px;
}
.variant{
    text-align: left;
    padding-left:40px ;
    width: 90vw;
    box-sizing: border-box;
    border-radius: 8px;
    padding-top: 16px;
    background:  rgba(240, 240, 240, 0.7);
    min-height: 60px;
    &.active{
        background:#fff;
    box-shadow: 0px 3px 10px rgba(50, 197, 116, 0.25);
    border: 2px solid #32C574;
    }
}
label{
        width: 95%;
    }
.list-price{
    font-size: 12px;
   color: #ccc;
   text-decoration: line-through;
   margin-bottom: 0.25rem;
}
.discount{
     font-size: 14px;
    color: #32C574;
    margin-bottom: 0.35rem;
}
</style>