<template>
  <div class="bottom-details mx-auto">
      <ul class="nav nav-pills mb-3" id="pills-tab" role="tablist">
  <li class="nav-item" role="presentation">
    <a class="nav-link active" id="pills-home-tab" data-toggle="pill" href="#1" role="tab" aria-controls="pills-home" aria-selected="true" v-on:click="changeTab(0)">Details</a>
  </li>
  <li class="nav-item" role="presentation">
    <a class="nav-link" id="pills-profile-tab" data-toggle="pill" href="#2" role="tab" aria-controls="pills-profile" aria-selected="false" v-on:click="changeTab(1)">How to take it</a>
  </li>
  <li class="nav-item" role="presentation">
    <a class="nav-link" id="pills-contact-tab" data-toggle="pill" href="#3" role="tab" aria-controls="pills-contact" aria-selected="false" v-on:click="changeTab(2)">Ingredients</a>
  </li>
</ul>
<div class="tab-content" id="pills-tabContent">
  <div class="tab-pane fade show" v-for="text in texts" :key="text" :id="text.id" :class="{ active: text.id === active}" role="tabpanel" aria-labelledby="pills-home-tab">
    <p :class="{overflow: text.show_all }" class="details-body">{{ text.body }}</p>
    <div class="row mx-0">
        <button @click="text.show_all = !text.show_all" class="btn btn-link ml-auto">
            Read 
            <span v-if="text.show_all">more</span>
            <span v-else>less</span>
        </button>
    </div>
  </div>
</div>
  </div>
</template>

<script>
export default {
    name:'Details',
    data : () =>{
        return {
            texts : [{id:0, title:'Details', show_all:false,body:'An amino acid found in tea, L-theanine is similar to glutamic acid, an excitatory neurotransmitter found in the central nervous system. A precursor to acetylcholine.'},
                {id:1, title:'Details',show_all:false,body:'Something Changed, L-theanine is similar to glutamic acid, an excitatory neurotransmitter found in the central nervous system. A precursor to acetylcholine.'},
                {id:2,title:'Details', show_all:false,body:'Again changed ,An amino acid found in tea, L-theanine is similar to glutamic acid, an excitatory neurotransmitter found in the central nervous system. A precursor to acetylcholine.'}
            ],
            active: 0
        }
    },
    methods: {
        changeTab : function(i){
            this.active = i
        }
    }
}
</script>

<style lang='scss'>
.bottom-details{
    width: 90vw;
    margin-bottom: 30vh;
}
.tab-pane{
    text-align: left;
    font-style: normal;
    font-weight: 500;
    font-size: 16px;
    line-height: 28px;
    color: rgba(29, 41, 26, 0.8);
}
.nav-link{
    padding: .5rem .8rem;
    color: #1D291A;
    font-weight: normal;
    &.active{
    color: #1D291A !important;
    font-weight: bold;
    background-color: #ffffff !important;
    border-bottom: 3px solid #F8D702;
}}
.overflow {
  text-overflow: ellipsis;
  white-space: nowrap;
  overflow: hidden;
}
</style>