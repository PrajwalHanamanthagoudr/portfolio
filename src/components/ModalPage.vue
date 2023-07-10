<template>
  <v-dialog v-model="dialog" max-width="500">
    <v-card color="#2e2e2e" rounded="lg">
      <v-toolbar color="#678EFF" title="Welcome to my portfolio website!"></v-toolbar>
      <v-card-text class="pa-10 text-white"
        >Explore my projects and skills to see how I can contribute to your next
        project.</v-card-text
      >
      <div class="py-4 px-5 text-start">
        <v-btn
          border
          class="text-none me-2"
          color="blue"
          text="View My Projects"
          variant="text"
          @click="dialog = false"
        ></v-btn>

        <v-btn
          border
          class="text-none me-2"
          color="blue"
          text="Learn More About Me"
          variant="text"
          @click="dialog = false"
        ></v-btn>
      </div>
    </v-card>
  </v-dialog>
</template>

<script>
export default {
  name: "ModalPage",
  data() {
    return {
      dialog: false,
    };
  },

  mounted() {
    setTimeout(() => {
      this.dialog = true;
    }, 20000);
  },

  methods: {},
};
</script>

<style></style>
