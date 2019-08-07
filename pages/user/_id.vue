<template>
  <div>
    <profile></profile>
    <br />
    <user-collection></user-collection>
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
  created() {},
  computed: {
    id() {
      return this.$route.params.id;
    }
  }
};
</script>

<style>
</style>
