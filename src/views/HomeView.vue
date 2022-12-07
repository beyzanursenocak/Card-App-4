<template>
  <v-container class="grey lighten-5" >
  <v-grid> 
    <v-row class="d-flex justify-content-between">

      <v-col cols="6" md="6">
        <ProductSection :product="products" @switch="switchImage"/>
        
      </v-col>
      <v-col cols="6">
        <v-form ref="form" v-model="valid" lazy-validation>
          <h3 style="color: green">Edit Form</h3>
          <v-text-field
            v-model="products.image"
            :rules="imageRules"
            label="Image"
            required>
        </v-text-field>

        <v-text-field
            v-model="products.title"
            :rules="titleRules"
            label="Title"
            required>
        </v-text-field>

          <v-text-field
            v-model="products.subtitle"
            :rules="subtitleRules"
            label="Subtitle"
            required
          >
          
        </v-text-field>

        <v-text-field
            v-model="products.text"
            :rules="text"
            label="Text"
            required
          >
        </v-text-field>

          <v-btn
            style="background-color: lightgreen"
            class="mx-2"
            @click="reset"
            elevation="24"
            rounded
          >
            Reset Form
          </v-btn>
        </v-form>
      </v-col>
    </v-row>
  </v-grid>
  </v-container>
</template>

<script>
import ProductSection from "./../components/ProductSection.vue";
export default {
  components: {
    ProductSection,
  },
  data: () => ({
    valid: true,
    image: "",
    imageRules: [
      (v) => !!v || "Image is required",
      (v) =>
        (v && v.length <= 1000) || "Image must be less than 1000 characters",
    ],
    titleRules: [
      (v) => !!v || "Title is required",
      (v) => /.+@.+\..+/.test(v) || "Title must be valid",
    ],
    subtitle: "",
    subtitleRules: [
      (v) => !!v || "Subtitle is required",
      (v) => /.+@.+\..+/.test(v) || "Subtitle must be valid",
    ],
    text: "",
    textRules: [
      (v) => !!v || "Text is required",
      (v) => /.+@.+\..+/.test(v) || "Text must be valid",
    ],
    products: 
  {
          title: " Top western road trips",
          image: "https://i.picsum.photos/id/1080/200/300.jpg?hmac=3jCG4X8ni9cpiEppj6KVvqhpJ_owIFtDQOABJmhG1I0", 
          subtitle: "1,000 miles of wonder",
          text: "I'm a thing. But, like most politicians, he promised more than he could deliver. You won't have time for sleeping, soldier, not with all the bed making you'll be doing. Then we'll go with that data file! Hey, you add a one and two zeros to that or we walk! You're going to do his laundry? I've got to find a way to escape.",
        },
  }),
  methods: {
    reset() {
      this.$refs.form.reset();
    },
    switchImage(url){
      console.log(url)
      this.products.image = url
    }
  },
};
</script>