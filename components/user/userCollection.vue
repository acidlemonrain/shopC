<template>
  <v-container>
    <div style="position:relative">
      <v-layout column justify-center align-content-center>
        <div class="absolute text-center mask">
          <h4>Lorem ipsum dolor sit.</h4>
          <v-btn>lorms</v-btn>
        </div>
        <img src="https://picsum.photos/1200/650" alt width="100%" class="cover" />
      </v-layout>
    </div>
  </v-container>
</template>

<script>
export default {};
</script>

<style scoped>
.mask {
  height: 100%;
  width: 100%;
  background-color: rgba(0, 0, 0, 0.596);
}
</style>
