<template>
  <v-container>
    <div v-show="isloaded">
      <v-list v-for="n in 10" :key="n">
        <v-list-item>
          <v-container>
            <v-layout>
              <img
                :src="'https://picsum.photos/'+(1200+3*15)+'/'+(600+(n%6)*15)"
                width="70px"
                class="rounded cover img"
                height="70px"
              />

              <v-card outline class="ml-5 pa-3">
                <h4>Lemon run: 2019-09-09 18:06pm</h4>Lorem iv-cardsu Lorem ipsum dolor sit amet consectetur adipisicing elit. Repudiandae, in possimus. m dolor sit amet consectetur adipisicing elit. Dolore, facere molestiae!
              </v-card>
            </v-layout>
          </v-container>
        </v-list-item>
      </v-list>
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
      length: 10,
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
        this.spanner += 10;
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
