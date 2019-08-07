<template>
  <div>
    <v-layout wrap>
      <v-flex md6 xs12>
        <v-container>
          <img
            :src="'https://picsum.photos/'+(1200+3*15)+'/'+(600+(this.id%6)*15)"
            width="100%"
            class="cover"
            alt
          />
        </v-container>
      </v-flex>
      <v-flex md6 xs12>
        <v-container>
          <h2>author : lemon jump</h2>
          <p>des : Lorem ipsum dolor sit amet consectetur adipisicing elit. Eveniet tempore velit assumenda alias perspiciatis illum, quibusdam neque repudiandae inventore in odit maiores omnis quo nostrum. Recusandae necessitatibus officiis corporis esse nisi quo aperiam?</p>

          <div>
            <v-rating v-model="rating"></v-rating>
          </div>
          <br />
          <br />
          <v-card-actions bottom>
            <v-spacer></v-spacer>
            <v-btn>likes</v-btn>
            <v-btn>add to cart</v-btn>
          </v-card-actions>
        </v-container>
      </v-flex>
    </v-layout>
    <hr />
    <comment></comment>
  </div>
</template>

<script>
import comment from "~/components/item/comment";
export default {
  components: {
    comment
  },
  computed: {
    id() {
      return this.$route.params.id;
    }
  },
  data() {
    return {
      rating: Math.round(Math.random() * 5)
    };
  },
  mounted() {}
};
</script>

<style>
</style>
