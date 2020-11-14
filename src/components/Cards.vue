<template>
  <div>
    <div ref="scrollable" class="scrollable" data-posx="0" :style="{'transform':'translateX(0px)'}">
      <div class="card-item" v-for="card in cards" v-bind:key="card.id">
        <CardItem  v-bind:card="card" v-on:showpopup="$emit('showpopup',card.id)" />
      </div>
    </div>
  </div>
</template>

<script>
import CardItem from './CardItem.vue'
export default {
  name: "Cards",
  components: {
    CardItem,
  },
  props: ["cards","direction"],
  watch: { 
    direction: function(newVal) {
      const element= this.$refs.scrollable;
      const width=element.offsetWidth;
      let X = element.dataset.posx;
      if(newVal=="left") {
        if(X!=0) 
        X--;
      }
      else {
        if(X<(this.cards.length-1))  
        X++;
      }
      const newX= -(width) * X;
      element.dataset.posx=X;
      element.style.transform="translateX("+newX+"px)"; 
    }
  }
}
</script>

<style  scoped>
.card-item {
  max-width: 95%;
  width: 386px;
  padding: 10px;
  border-radius: 10px;
  background: white;
  margin: 0 10px;
  display: inline-block;
}
.scrollable {
  transition: transform cubic-bezier(0.075, 0.82, 0.165, 1) 0.6s;
}
@media only screen and (max-width: 1100px) {
  .card-item {
     margin: 0 10px;
  }
}
@media only screen and (max-width: 760px) {
  .card-item {
    max-width: 96%;
    margin: 0 2%;
  }
   
}

</style>