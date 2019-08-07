<template>
  <div>
    <div v-show="isloaded">
      <v-carousel hide-delimiters v-model="model">
        <v-carousel-item v-for="n in 5" :key="n">
          <div class="slide">
            <div class="slide-text">
              <h4>author : Lorem, ipsum.</h4>
              <h5>price: $ {{Math.round(Math.random()*100)}}</h5>
              <v-layout>
                <v-spacer></v-spacer>
                <v-btn text :to="'item/'+n" route>More</v-btn>
              </v-layout>
            </div>
            <img :src="'https://picsum.photos/1300/'+(600+n*25)" class="slideimg img" />
          </div>
        </v-carousel-item>
      </v-carousel>
      <v-layout justify-center class="mt-2">
        <div v-for="n in 5" :key="n" class="mx-2 pointer">
          <img
            @click="model=n"
            :src="'https://picsum.photos/1300/'+(600+n*25)"
            style="object-fit:cover"
            height="50px"
            width="50px"
          />
        </div>
      </v-layout>
    </div>
    <div v-show="!isloaded">
      <v-progress-linear v-model="spanner" color="blue-grey" height="25" reactive>
        <template v-slot="{ value }">
          <strong>{{ Math.ceil(value) }}%</strong>
        </template>
      </v-progress-linear>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      model: 0,
      length: 5,
      loaded: 0,
      isloaded: false,
      spanner: 0
    };
  },
  props: ["items"],

  mounted() {
    const imgs = document.getElementsByTagName("img");
    for (let index = 0; index < imgs.length; index++) {
      imgs[index].onload = () => {
        ++this.loaded;
        this.spanner += 20;
      };
    }
  },
  watch: {
    loaded(to) {
      if (to == 5) {
        this.isloaded = true;
      }
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
 

 