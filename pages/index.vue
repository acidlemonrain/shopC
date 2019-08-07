<template>
  <div>
    <v-container>
      <search></search>
      <br />

      <recomment></recomment>
      <br />
      <discover></discover>
      <br />

      <br />
      <author-collection></author-collection>
    </v-container>
  </div>
</template>

<script>
import search from "~/components/index/search";
import recomment from "~/components/index/recomment";
import discover from "~/components/index/discover";
import authorCollection from "~/components/index/authorCollection";
import comment from "~/components/item/comment";
import axios from "axios";

export default {
  data() {
    return {
      items: []
    };
  },
  components: {
    recomment,
    search,
    discover,
    authorCollection,
    comment
  },
  created() {
    axios.get("https://picsum.photos/v2/list?limit=5").then(res => {
      this.items = res.data;
    });
  }
};
</script>
