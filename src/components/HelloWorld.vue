<template>
  <div>
    <v-carousel
      cycle
      :height="cheight"
      v-resize="method1"
      delimiter-icon="mdi-minus"
      hide-delimiter-background
      show-arrows-on-hover
    >
      <v-carousel-item v-for="(slide, i) in slides" :key="i">
        <v-sheet :color="colors[i]" height="100%">
          <v-row class="fill-height" align="center" justify="center">
            <div class="display-1">{{ slide }} Slide</div>
          </v-row>
        </v-sheet>
      </v-carousel-item>
    </v-carousel>

    <v-form v-model="valid" dark>
      <v-container>
        <p class="text-center text-uppercase font-weight-medium">Wall 1</p>
        <v-row>
          <v-col cols="12" md="6">
            <v-text-field
              v-model="width1"
              :rules="widthRules"
              color="purple darken-4"
              label="Width"
              type="text"
              inputmode="numeric"
              pattern="[0-9]*"
              required
            ></v-text-field>
          </v-col>

          <v-col cols="12" md="6">
            <v-text-field
              v-model="height1"
              :rules="heightRules"
              color="purple darken-4"
              label="Height"
              type="text"
              inputmode="numeric"
              required
            ></v-text-field>
          </v-col>
        </v-row>

        <p class="text-center text-uppercase font-weight-medium">Wall 2</p>
        <v-row>
          <v-col cols="12" md="6">
            <v-text-field
              v-model="width2"
              :rules="widthRules"
              color="purple darken-4"
              label="Width"
              type="text"
              inputmode="numeric"
              pattern="[0-9]*"
              required
            ></v-text-field>
          </v-col>

          <v-col cols="12" md="6">
            <v-text-field
              v-model="height2"
              :rules="heightRules"
              color="purple darken-4"
              label="Height"
              type="text"
              inputmode="numeric"
              required
            ></v-text-field>
          </v-col>
        </v-row>

        <p class="text-center text-uppercase font-weight-medium">Result</p>
        <v-row>
          <v-col cols="12" md="6">
            <v-text-field
              v-model="area"
              label="Area"
              type="text"
              :disabled="true"
            ></v-text-field>
          </v-col>

          <v-col cols="12" md="6">
            <v-text-field
              v-model="rolls"
              label="Rolls Needed"
              type="text"
              :disabled="true"
            ></v-text-field>
          </v-col>
        </v-row>

        <v-row>
          <v-col cols="12">
            <div class="text-center">
              <v-btn class="ma-2" tile color="purple darken-4" dark
                >Submit</v-btn
              >
            </div>
          </v-col>
        </v-row>
      </v-container>
    </v-form>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",

  data: () => ({
    colors: [
      "indigo",
      "warning",
      "pink darken-2",
      "red lighten-1",
      "deep-purple accent-4",
    ],
    slides: ["First", "Second", "Third", "Fourth", "Fifth"],
    cheight: "400",
    valid: false,
    width1: "",
    height1: "",
    width2: "",
    height2: "",
    area: "",
    rolls: "",
    widthRules: [
      (v) => !!v || "Width is required",
      (v) => v.length <= 10 || "Width must be less than 10 characters",
    ],
    heightRules: [
      (v) => !!v || "Height is required",
      (v) => v.length <= 10 || "Height must be less than 10 characters",
    ],
  }),

  mounted: function() {
    this.method1(); //method1 will execute at pageload
  },

  methods: {
    method1: function() {
      var isMobile = /iPhone|iPad|iPod|Android/i.test(navigator.userAgent);
      if (isMobile) {
        this.cheight = "250";
      } else {
        this.cheight = "400";
      }
    },
  },
};
</script>
