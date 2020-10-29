<template>
  <div class="row mx-0 sub-images">
      <div class="col-3" v-for="(image,i) in images" :key="i" v-on:click="changesActive(i)">
          <img :src="image" class="images" :class="{ active: i === active}"/>
      </div>
  </div>
</template>

<script>
export default {
    name:'SubImages',
    data: function(){
        return {
            images:["https://ik.imagekit.io/enactus/Rectangle_12__1__Q7RJGFlUx.png","https://ik.imagekit.io/enactus/Rectangle_12__1__Q7RJGFlUx.png","https://ik.imagekit.io/enactus/Rectangle_12__1__Q7RJGFlUx.png","https://ik.imagekit.io/enactus/Rectangle_12__1__Q7RJGFlUx.png"],
            active:1
        }},
    methods:{
        changesActive: function(i) {
           this.active = i
        }
    }
}
</script>

<style lang='scss' scoped>
.sub-images{
    margin-top: 20px;
    margin-bottom: 24px;
}
.images{
    max-width: 100%;
    border: 3px solid #FFFFFF;
    filter: drop-shadow(0px 3px 10px rgba(0, 0, 0, 0.11));
    border-radius: 8px;
    &.active {
    border: 3px solid #F8D702;
    }
}
.col-3{
    padding: 0;
}
</style>