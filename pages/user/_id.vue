<template>
  <div>
    <profile></profile>
    <br />
    <div>
      <div v-show="isloaded">
        <v-layout wrap>
          <v-flex v-for="n in 5" :key="n" xs12 md6>
            <user-collection @load="handleload"></user-collection>
          </v-flex>
        </v-layout>
      </div>
      <div v-show="!isloaded" class="text-center">
        <v-progress-circular
          :rotate="360"
          :size="100"
          :width="15"
          :value="loaded*20"
          color="teal"
        >{{ loaded*20 }}</v-progress-circular>
      </div>
    </div>
  </div>
</template>

<script>
import userCollection from "~/components/user/userCollection";
import profile from "~/components/user/profile";
export default {
  components: {
    profile,
    userCollection
  },
  data() {
    return {
      loaded: 0,
      isloaded: false
    };
  },
  created() {},
  computed: {
    id() {
      return this.$route.params.id;
    }
  },
  methods: {
    handleload() {
      this.loaded++;
    }
  },
  watch: {
    loaded(to) {
      if (to === 5) {
        this.isloaded = true;
      }
    }
  }
};
</script>

<style>
</style>
