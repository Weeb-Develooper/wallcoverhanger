<template>
  <v-app>
    <v-app-bar absolute color="primary" elevate-on-scroll v-resize="method1">
      <v-toolbar-title class="font-weight-medium">
        WallcoverHanger
      </v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn
        text
        class="d-none d-xl-flex d-lg-flex d-xl-none d-md-none d-lg-flex d-sm-none d-md-flex d-sm-flex mr-2"
      >
        <span class="mr-2">Portfolio</span>
      </v-btn>

      <v-switch
        class="d-none d-xl-flex d-lg-flex d-xl-none d-md-none d-lg-flex d-sm-none d-md-flex d-sm-flex mr-2"
        v-model="$vuetify.theme.dark"
        hide-details
        :label="`${switch1}`"
        @change="changeState"
      ></v-switch>

      <v-menu bottom left v-if="menu == true">
        <template v-slot:activator="{ on }">
          <v-btn icon v-on="on" class="">
            <v-icon>mdi-menu</v-icon>
          </v-btn>
        </template>
        <v-list shaped nav dense>
          <v-list-item>
            <v-btn text>
              <span class="mr-2">Portfolio</span>
            </v-btn>
          </v-list-item>

          <v-list-item>
            <v-switch
              v-model="$vuetify.theme.dark"
              hide-details
              :label="`${switch1}`"
              @change="changeState"
            ></v-switch>
          </v-list-item>
        </v-list>
      </v-menu>
    </v-app-bar>

    <v-content>
      <router-view></router-view>
    </v-content>

    <v-footer class="pa-0" :elevation="5">
      <v-card flat tile width="100%" color="primary">
        <v-card-text class="text-center">
          © <strong>WallcoverHanger</strong> {{ new Date().getFullYear() }}
        </v-card-text>
      </v-card>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  name: "App",

  components: {},

  data: () => ({
    switch1: "Light",
    menu: true,
    m: "dd",
  }),

  mounted: function() {
    this.method1(); //method1 will execute at pageload
  },

  methods: {
    //changes theme manually
    changeState() {
      if (this.switch1 == "Light" && this.$vuetify.theme.dark == true) {
        this.switch1 = "Dark";
      } else {
        this.switch1 = "Light";
      }
    },

    method1: function() {
      var isMobile = /iPhone|iPad|iPod|Android/i.test(navigator.userAgent);
      if (isMobile) {
        this.menu = true;
      } else {
        this.menu = false;
      }
    },
  },
};
</script>
