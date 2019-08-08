<template>
  <v-app dark>
    <v-app-bar fixed app>
      <v-toolbar-title>
        <v-btn to="/">home</v-btn>
      </v-toolbar-title>

      <v-spacer></v-spacer>
      <v-list class="hidden-sm-and-down">
        <v-btn large text>分类</v-btn>
        <v-btn large text>促销</v-btn>
      </v-list>
      <v-spacer></v-spacer>

      <v-menu text="more" offset-y>
        <template v-slot:activator="{ on }">
          <v-btn large text v-on="on">用户</v-btn>
        </template>
        <v-list>
          <v-list-item>
            <v-btn text>账户</v-btn>
          </v-list-item>
          <v-list-item>
            <v-btn text>余额</v-btn>
          </v-list-item>
        </v-list>
      </v-menu>
      <div class="hidden-md-and-up">
        <v-menu offset-y>
          <template v-slot:activator="{ on }">
            <v-btn text v-on="on" v-icon>
              <v-icon>mdi-dots-vertical</v-icon>
            </v-btn>
          </template>
          <v-list>
            <v-list-item>
              <v-btn text>分类</v-btn>
            </v-list-item>
            <v-list-item>
              <v-btn text>促销</v-btn>
            </v-list-item>
          </v-list>
        </v-menu>
      </div>
    </v-app-bar>
    <v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>

    <v-footer fixed app>
      <span>&copy; 2019</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {};
  }
};
</script>
<style>
.absolute {
  position: absolute;
}
.pointer {
  cursor: pointer;
}
.cover {
  object-fit: cover;
}
.rounded {
  border-radius: 50%;
}
.pop {
  transition: all 0.4s;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.445);
}
.pop:hover {
  transform: rotate(-4deg) scale(0.9);
  box-shadow: 19px 4px 10px rgba(0, 0, 0, 0.438);
}
</style>
 