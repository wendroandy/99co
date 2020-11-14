<template>
  <div>
    <div
      class="image-wrapper"
      :style="{ 'background-image': 'url(' + card.image + ')' }"
    ></div>
    <div class="desc-wrapper">
      <div class="description">
        <span class="sale" v-if="card.sale">Dijual</span>
        <span class="nego" v-if="card.nego">Nego</span>
        <img class="fav" src="../assets/icon/love.svg" />
      </div>
      <div class="price">
        <span class="bold">{{ card.price }}</span> Cicilan
        <span>{{ card.cicilan }}</span>
      </div>
      <div class="asset">
        <div class="bed">{{ card.bed }} K.Tidur</div>
        <div class="bath">{{ card.bath }} K.Mandi</div>
        <div class="building">{{ card.luasBangunan }}</div>
        <div class="area">{{ card.luasArea }}</div>
      </div>
      <button v-on:click="$emit('showpopup',card.id);">Lihat Detail</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "CardItem",
  props: ["card"],
};
</script>
<style scoped>
.desc-wrapper {
  padding: 10px;
}
.image-wrapper {
  height: 260px;
  width: 100%;
  background-size: cover;
  background-position: center;
  border-top-left-radius: 10px;
  border-top-right-radius: 10px;
  margin-bottom: 8px;
}
.description,
.price,
.asset {
  margin-bottom: 20px;
  white-space: normal;
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

</style>