<template>
  <div class="card-item"> 
    <div class="popup-content" v-if="showContent" >
      <div
        class="image-wrapper"
        :style="{ 'background-image': 'url(' + cardpopup.image + ')' }"
      ></div>
      <div class="desc-wrapper">
        <div class="description">
          <span class="sale" v-if="cardpopup.sale">Dijual</span>
          <span class="nego" v-if="cardpopup.nego">Nego</span>
          <img class="fav" src="../assets/icon/love.svg" />
        </div>
        <div class="title">
          <h3>{{ cardpopup.title }}</h3>
          <p>{{ cardpopup.address }}</p>
        </div>
        <div class="price">
          <span class="bold">{{ cardpopup.price }}</span> Cicilan
          <span>{{ cardpopup.cicilan }}</span>
        </div>
        <div class="asset">
          <div class="bed">{{ cardpopup.bed }} K.Tidur</div>
          <div class="bath">{{ cardpopup.bath }} K.Mandi</div>
          <div class="building">{{ cardpopup.luasBangunan }}</div>
          <div class="area">{{ cardpopup.luasArea }}</div>
        </div>
        <button v-on:click="showMap= true;showContent= false;">Lihat Peta</button>
      </div>
    </div>
    <div class="popup-map" v-if="showMap" v-on:close="viewMap = false">
      <div
        class="image-wrapper"
        :style="{ 'background-image': 'url(' + cardpopup.map + ')' }"
      ></div>
      <div class="desc-wrapper">
        <div class="title">
          <h3>{{ cardpopup.address }}</h3>
        </div>
        <p>{{ cardpopup.desc }}</p>
        <button v-on:click="showMap = false;showContent=true">Tutup</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CardPopUp",
  props: ["cardpopup"],
  data() {
    return {
      showContent: true,
      showMap: false,
    };
  }
};
</script>
<style scoped>
.card-item {
  max-width: 95%;
  width: 780px;
 
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
.popup-content,.popup-map {

  background:white;
  width:100%;
   padding: 16px 16px 8px 16px;
  border-radius: 10px;
}
.desc-wrapper {
  padding: 16px;
}
.image-wrapper {
  height: 390px;
  width: 100%;
  background-size: cover;
  background-position: center;
  border-top-left-radius: 10px;
  border-top-right-radius: 10px;
  margin-bottom: 8px;
}
.description,
.price,
.asset,
.title {
  margin-bottom: 20px;
}
.description > * {
  width: 64px;
  padding: 4px 0px;
  display: inline-block;
  text-align: center;
  font-family: "ADB";
  margin-right: 10px;
  font-size: 12px;
}
.title h3 {
  font-size: 16px;
  font-family: "ADB";
  margin-bottom: 8px;
}
.sale {
  background: #e9eef2;
  border-radius: 3px;
}
.nego {
  background: #50b782;
  color: white;
  border-radius: 10px;
}
.fav {
  width: 25px;
  float: right;
  margin-top: -4px;
  display: block;
}
.asset > * {
  display: inline-block;
  margin-right: 12px;
  height: 20px;
  background-repeat: no-repeat;
  background-position: 0px 2px;
  font-family: "ADB";
  padding-left: 18px;
}
.asset .bed {
  background-image: url("../assets/icon/Kamar Tidur.svg");
}
.asset .bath {
  background-image: url("../assets/icon/Kamar mandi.svg");
}
.asset .building {
  background-image: url("../assets/icon/Luas Bangunan.svg");
}
.asset .area {
  background-image: url("../assets/icon/Luas Tanah.svg");
}
.bold {
  font-family: "AB";
  font-size: 16px;
}
button {
  background: #50b782;
  width: 100%;
  border: 0;
  border-radius: 3px;
  padding: 10px 0;
  color: white;
  cursor: pointer;
  transition: all cubic-bezier(0.075, 0.82, 0.165, 1) 0.6s;
}
button:hover {
  background: #239056;
  font-weight: bold;
}
.popup-map .desc-wrapper p {
  min-height: 153px;
}
</style>