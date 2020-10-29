<template>
    <div class="rating mx-auto row">
        <div class="col-8">
             <star-rating inactive-color="#F2C94C45" border-color="#fff" :increment="0.1" :show-rating="false" :inline="true" :read-only="true" :border-width="2" :star-size="35" :rating="rating" :rounded-corners="true" :star-points="[23,2, 14,17, 0,19, 10,34, 7,50, 23,43, 38,50, 36,34, 46,19, 31,17]"></star-rating>
        </div>
        <div class="col-4 rating-words m-auto p-0">
            {{rating}} stars
        </div>
    </div>
</template>

<script>
import StarRating from 'vue-star-rating'
export default {
    name: 'Rating',
    components: {
    StarRating
    },
    data: ()=>{
        return{
            rating: 4.4
        }
    },
    methods: {
    setRating: function(rating) {
      this.rating = "You have Selected: " + rating + " stars";
    },
    showCurrentRating: function(rating) {
      this.currentRating = (rating === 0) ? this.currentSelectedRating : "Click to select " + rating + " stars"
    },
    setCurrentSelectedRating: function(rating) {
      this.currentSelectedRating = "You have Selected: " + rating + " stars";
    }
  },
}
</script>

<style lang="scss">
.rating{
    width: 90vw;
    margin-top: 8px;
    margin-bottom: 16px;
}
.rating-words{
    color: rgba(29, 41, 26, 0.8);
    font-weight: 100;
    font-size: 20px;
}
</style>