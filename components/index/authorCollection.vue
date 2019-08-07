<template>
  <div>
    <v-card flat class="pa-3">
      <div class="text-center">
        <img
          :src="'https://picsum.photos/1300/'+(600+3*25)"
          class="rounded cover"
          height="100px"
          width="100px"
        />
        <h3>Lemon</h3>
      </div>
      <hr />
      <v-layout v-show="isloaded" wrap justify-center>
        <v-flex xs12 md3 class="ma-3" v-for="(n) in 5" :key="n">
          <v-container>
            <img
              :src="'https://picsum.photos/1300/'+(600+n*35)"
              width="100%"
              height="120px"
              class="acimg cover"
              alt
            />
          </v-container>
        </v-flex>
      </v-layout>
      <div v-show="!isloaded">
        <v-progress-linear v-model="spanner" color="blue-grey" height="25" reactive>
          <template v-slot="{ value }">
            <strong>{{ Math.ceil(value) }}%</strong>
          </template>
        </v-progress-linear>
      </div>
      <v-card-actions>
        <v-spacer></v-spacer>
        <v-btn>More</v-btn>
      </v-card-actions>
    </v-card>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      items: [],
      spanner: 0,
      loaded: 0,
      isloaded: false
    };
  },
  created() {
    axios.get("https://picsum.photos/v2/list?limit=5").then(res => {
      this.items = res.data;
    });
  },
  mounted() {
    const imgs = document.getElementsByClassName("acimg");
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

<style>
</style>
