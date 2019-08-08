<template>
  <v-container>
    <div class="pa-2">
      <v-card>
        <div style="position:relative">
          <div class="absolute text-center mask">
            <div class="flex">
              <h4>Lorem ipsum dolor sit.</h4>
              <v-btn outlined>查看</v-btn>
            </div>
          </div>
          <div style="height:300px">
            <img
              ref="img"
              :src="'https://picsum.photos/1300/'+(600+size*25)"
              alt
              width="100%"
              class="cover"
              height="100%"
            />
          </div>
        </div>
      </v-card>
    </div>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      size: 1,
      loaded: 0,
      isloaded: false
    };
  },
  created() {
    this.size = Math.floor(Math.random() * 15);
  },
  mounted() {
    this.$refs.img.onload = () => {
      this.$emit("load");
    };
  }
};
</script>

<style scoped>
.mask {
  height: 100%;
  width: 100%;

  transition: all 0.4s;
}
.mask:hover .flex {
  opacity: 1;
  background-color: rgba(0, 0, 0, 0.596);
}
.mask:hover {
  background-color: rgba(0, 0, 0, 0);
}
.flex {
  transition: opacity 0.4s;
  display: flex;
  flex-flow: column;
  justify-items: center;
  flex-wrap: wrap;
  justify-content: center;
  align-content: center;
  height: 100%;
  opacity: 0;
}
</style>

