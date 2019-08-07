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
      <v-layout wrap justify-center>
        <v-flex xs12 md3 class="ma-3" v-for="(item,i) in items" :key="item.id">
          <v-container>
            <img
              :src="'https://picsum.photos/1300/'+(600+i*35)"
              width="100%"
              height="120px"
              class="cover"
              alt
            />
          </v-container>
        </v-flex>
      </v-layout>
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
      items: []
    };
  },
  created() {
    axios.get("https://picsum.photos/v2/list?limit=5").then(res => {
      this.items = res.data;
    });
  }
};
</script>

<style>
</style>
