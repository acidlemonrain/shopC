<template>
  <div>
    <discover :items="items"></discover>
    <c></c>
  </div>
</template>

<script>
import axios from "axios";
import discover from "~/components/index/discover";
import c from "~/components/item/comment";
export default {
  data() {
    return {
      items: []
    };
  },
  components: {
    discover,
    c
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
