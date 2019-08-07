<template>
  <v-container>
    <div v-show="isloaded">
      <v-layout v-for="n in 5" :key="n">
        <v-flex md6>
          <v-container>
            <img
              :src="'https://picsum.photos/'+(1200+3*15)+'/'+(600+(n%6)*15)"
              width="100%"
              class="cover img"
            />
          </v-container>
        </v-flex>
        <v-flex md6>
          <v-container>
            <h3>Lorem, ipsum dolor.</h3>
            <p>Lorem, ipsum dolo Lorem ipsum dolor sit amet consectetur adipisicing elit. Fugit nam natus earum sapiente expedita ea consequatur eum fugiat tempore facere eligendi, dignissimos, necessitatibus numquam id. Illo earum ex inventore numquam corporis culpa ipsa.</p>
          </v-container>
        </v-flex>
      </v-layout>
    </div>
    <div v-show="!isloaded">
      <v-progress-linear v-model="spanner" color="blue-grey" height="25" reactive>
        <template v-slot="{ value }">
          <strong>{{ Math.ceil(value) }}%</strong>
        </template>
      </v-progress-linear>
    </div>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      length: 5,
      loaded: 0,
      isloaded: false,
      spanner: 0
    };
  },
  computed: {},
  mounted() {
    const imgs = document.getElementsByClassName("img");
    for (let index = 0; index < imgs.length; index++) {
      imgs[index].onload = () => {
        this.loaded++;
        this.spanner += 20;
      };
    }
  },
  watch: {
    loaded(to) {
      if (to == this.length) {
        this.isloaded = true;
      }
    }
  }
};
</script>

<style>
</style>
