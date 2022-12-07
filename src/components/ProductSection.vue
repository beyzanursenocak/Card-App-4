<template>
  <v-grid>
    <v-row>
      <v-col>
        <v-card
          class="mx-auto mt-5"
          max-width="344"
          style="background-color: whitesmoke"
        >
          <iframe height="304px" width="206" :src="product.image"></iframe>

          <!-- {{product.image}}
          <v-img height="200px" :src="product.image"></v-img> -->
          <v-row justify="space-around">
            <v-card-title style="color: darkred">
              {{ product.title }}
            </v-card-title>

            <v-card-subtitle style="color: brown">
              {{ product.subtitle }}
            </v-card-subtitle>
          </v-row>

          <v-card-actions>
            <v-btn @click="show = !show" style="background-color: rosybrown">
              Explore
            </v-btn>
            <v-spacer></v-spacer>
            <v-btn @click="switchImage" style="background-color: lightcoral">
              Change Image
            </v-btn>
            <v-spacer></v-spacer>
            <v-btn icon @click="show = !show">
              <v-icon>{{
                show ? "mdi-chevron-up" : "mdi-chevron-down"
              }}</v-icon>
            </v-btn>
          </v-card-actions>

          <v-expand-transition>
            <div v-show="show">
              <v-divider></v-divider>

              <v-card-text style="color: brown"
              >
                {{ product.text }}
              </v-card-text>
            </div>
          </v-expand-transition>
        </v-card>
      </v-col>
    </v-row>
  </v-grid>
</template>

<script>
export default {
  props: {
    product: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      show: false,
    };
  },
  methods: {
    switchImage() {
      let randomNummber = Math.floor(Math.random() * 500);
      console.log(randomNummber);
      let url = `https://picsum.photos/seed/${randomNummber}/200/300`;
      console.log(url);
      this.$emit("switch", url);
    },
  },
};
</script>

