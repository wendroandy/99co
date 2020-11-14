<template>
  <div id="app">
    <img src="./assets/bg.png" class="image-bg"/>
    <div class="wrapper">
      <div class="text">
        <h1>Start Your Journey</h1>
        <p>Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.</p>
      </div>
      <div class="slider">
        <div class="arrow left" v-on:click="slide('left')"><img src="./assets/icon/arrow.svg"/></div>
          <Cards class="card-wrapper" v-bind:direction="direction" v-bind:cards="cards" v-on:showpopup="onShowPopup" />
        <div class="arrow right" v-on:click="slide('right')"><img src="./assets/icon/arrow left.svg"/></div>
      </div>
    </div>
    <div class="popup-bg" v-if="showPopup" v-on:click="showPopup=false" ></div>
    <CardPopUp v-if="showPopup" v-bind:cardpopup="showPopup"/>
  </div>
</template>

<script>
import Cards from './components/Cards.vue'
import CardPopUp from './components/CardPopUp.vue'
export default {
  name: 'App',
  components: {
    Cards,
    CardPopUp
  },
  data() {
    return {
      cards: [
        {
          id: 1,
          title: "Rumah minimalis dijual di Bandung Jawa Barat",
          address: "Jl Sukajadi 1 Jawa Barat",
          image: "https://upload.wikimedia.org/wikipedia/commons/2/2e/Alvord_House.jpg",
          map: "https://www-static.weddingbee.com/wp-content/uploads/2009/04/baton-rouge-map.jpg",
          desc: "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.",
          sale : true,
          nego: true,
          price: "Rp 326 jt",
          cicilan: "Rp 2,61 jt/bln",
          bed: 2,
          bath: 2,
          luasBangunan: "65m2",
          luasArea: "65m2",
          favourite: false
        },
         {
          id: 2,
          title: "Rumah minimalis dijual di Bandung Jawa Barat",
          image: "https://upload.wikimedia.org/wikipedia/commons/e/e9/John_D_Ballard_House.jpg",
          map: "https://www-static.weddingbee.com/wp-content/uploads/2009/04/baton-rouge-map.jpg",
          desc: "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.",
          address: "Jl Sukajadi 2 Jawa Barat",
          sale : true,
          nego: true,
          price: "Rp 327 jt",
          cicilan: "Rp 3,61 jt/bln",
          bed: 3,
          bath: 3,
          luasBangunan: "60m2",
          luasArea: "60m2",
          favourite: false
        }
      ],
      showPopup: false,
      direction: "none",
    }
  },
   methods : {
     onShowPopup(id) {
       this.showPopup=this.cards[id-1];
     },
     slide(direction){
       this.direction=direction;
     }
  }
}
</script>

<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'AR', Arial, Helvetica, sans-serif;
  font-size:14px;
}
.image-bg {
  position: absolute;
  width: 100%;
  bottom: 0;
  left:0;
}
html {
  height: 100%;
}
body {
  background: rgb(119,61,221);
  background: linear-gradient(90deg, rgba(119,61,221,1) 0%, rgba(107,67,225,1) 100%);
  min-height: 100%;
  position: relative;
  padding-top: 200px;
}
@font-face {
  font-family: "AB";
  src: local("AvenirNext-Bold.woff"),
   url(./fonts/AvenirNext-Bold.woff) format("woff");
}
@font-face {
  font-family: "ADB";
  src: local("AvenirNext-DemiBold.woff"),
   url(./fonts/AvenirNext-DemiBold.woff) format("woff");
}
@font-face {
  font-family: "AR";
  src: local("AvenirNext-Regular.woff"),
   url(./fonts/AvenirNext-Regular.woff) format("woff");
}
.wrapper {
  width: 1100px;
  margin: 0 auto;
  position:relative;
}
.slider {
  width: 400px;
  display: block;
  float: left;
  position: relative; 
  max-width: calc(100% - 100px)
}

.text {
  width: calc(100% - 400px);
  display: block;
  float: left;
  color: white;
  padding-right: 200px; 
}
.text h1 {
  font-family: "AB";
  font-size: 50px
}
.arrow {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  cursor: pointer;
  width: 40px;
  height: 40px;
  background: white;
  border-radius: 50%;
  padding: 9px 0;
  text-align: center;
}
.arrow:hover {
  transform: translateY(-55%);
  transition: all cubic-bezier(0.075, 0.82, 0.165, 1) 0.6s;
}
.arrow.left{
  margin-left:-40px;
  left:0;
}
.arrow.right{
  margin-right:-40px;
  right: 0;
}
.card-wrapper {
  overflow: hidden;
  white-space: nowrap;
}
.popup-bg {
  position: absolute;
  top: 0;
  left: 0;
  background: rgba(0,0,0,0.5);
  width: 100%;
  height: 100%;
}
@media only screen and (max-width: 1100px) {
  body {
    padding-top: 20px;
  }
  .wrapper {
    width: 760px;
    text-align:center;
    margin: 0 auto;
  }
  .text {
    width: 100%;
    float: none;
    display: inline-block;
    padding:0 20px;
    margin-bottom: 20px;
  }
  .slider {
    display: inline-block;
    float: none;
  }
}
@media only screen and (max-width: 760px) {
  .wrapper {
    width: 100%;
  }
   
}
</style>
