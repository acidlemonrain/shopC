<template>
  <v-container>
    <div v-show="isloaded">
      <v-layout wrap v-for="(item,i) in items" :key="item.id">
        <v-flex xs12 md6>
          <v-container>
            <img
              width="100%"
              :src="'https://picsum.photos/'+(1200+i*15)+'/'+(600+i*15)"
              alt
              class="cover img"
            />
          </v-container>
        </v-flex>
        <v-flex xs12 md6>
          <v-container>
            <h3>author : {{item.author}}</h3>
            <p>des: Lorem ipsum dolor, sit amet consectetur adipisicing elit. Expedita eveniet quaerat ut ad laudantium recusandae cum inventore deleniti obcaecati doloribus aspernatur dolore fuga ipsum, vitae, optio nisi omnis accusantium neque voluptatibus sequi earum.</p>
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
  props: ["items"],
  data() {
    return {
      length: 5,
      isloaded: false,
      loaded: 0,
      spanner: 0
    };
  },
  mounted() {
    const imgs = document.getElementsByTagName("img");
    for (let index = 0; index < imgs.length; index++) {
      imgs[index].onload = () => {
        this.loaded++;
        this.spanner += 10;
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
