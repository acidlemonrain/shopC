<template>
  <div>
    <v-carousel hide-delimiters v-model="model">
      <v-carousel-item v-for="(item,i) in items" :key="item.email">
        <div class="slide">
          <div class="slide-text">
            <h4>author : {{item.author}}</h4>
            <h5>price: $ {{Math.round(Math.random()*100)}}</h5>
            <v-layout>
              <v-spacer></v-spacer>
              <v-btn text :to="'item/'+item.id" route>More</v-btn>
            </v-layout>
          </div>
          <img :src="'https://picsum.photos/1300/'+(600+i*25)" class="slideimg img" />
        </div>
      </v-carousel-item>
    </v-carousel>
    <v-layout justify-center class="mt-2">
      <div v-for="(item,i) in items" :key="item.email" class="mx-2 pointer">
        <img
          @click="model=i"
          :src="'https://picsum.photos/1300/'+(600+i*25)"
          style="object-fit:cover"
          height="50px"
          width="50px"
        />
      </div>
    </v-layout>
  </div>
</template>

<script>
export default {
  data() {
    return {
      model: 0
    };
  },
  props: ["items"],

  mounted() {
    const imgs = document.getElementsByClassName("img");
    for (let index = 0; index < imgs.length; index++) {
      imgs[index].onload = () => {
        alert(123);
      };
    }
  }
};
</script>

  <style scoped>
.slide {
  position: relative;
}
.slideimg {
}
.slide:hover .slide-text {
  opacity: 1;
}
.slide-text {
  transition: opacity 0.4s;
  position: absolute;
  z-index: 5;
  background-color: rgba(0, 0, 0, 0.397);
  text-align: center;
  width: 100%;
  padding: 5px;
  opacity: 0;
}
</style>
 

 