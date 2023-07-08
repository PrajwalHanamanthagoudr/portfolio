<template>
  <NavigationBar />
  <v-container class="text-center">
    <v-row class="text-white">
      <v-row>
        <v-col class="d-flex justify-center align-center">
          <div class="d-flex flex-column">
            <span class="text-start animate__animated animate__fadeInLeft">Full Stack Developer</span>
            <h1 style="font-size: 10rem!;" class="animate__animated animate__fadeInLeft animate__delay-1s">Hi, I'm <span style="color: #678EFF;">Prajwal</span></h1>
            <v-btn color="#687EFF" width="150" class="animate__animated animate__fadeInLeft animate__delay-2s">Download CV</v-btn>
          </div>
        </v-col>
      </v-row>
      <v-col>
        <v-img src="@/assets/t1.png" width="500" class="animate__animated animate__fadeInRight animate__delay-3s"
          style="background-image: linear-gradient(to bottom, #0040ff, #678EFF); border-radius: 50%;" cover></v-img>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import { defineComponent } from 'vue';

// Components
import NavigationBar from '@/components/NavigationBar.vue';

export default defineComponent({
  name: 'HomeView',

  components: {
    NavigationBar,
  },
});
</script>

<style>
.animate__animated {
  animation-duration: 1s;
  animation-fill-mode: both;
}

.animate__delay-1s {
  animation-delay: 1s;
}

.animate__delay-2s {
  animation-delay: 2s;
}

.animate__delay-3s {
  animation-delay: 3s;
}

@keyframes fadeInLeft {
  from {
    opacity: 0;
    transform: translateX(-100px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

@keyframes fadeInRight {
  from {
    opacity: 0;
    transform: translateX(100px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

.animate__fadeInLeft {
  animation-name: fadeInLeft;
}

.animate__fadeInRight {
  animation-name: fadeInRight;
}
</style>
