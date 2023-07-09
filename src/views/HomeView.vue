<template>
  <NavigationBar @scrollToSection="scrollToSection" />
  <v-container class="text-center" id="home">
    <v-row class="text-white">
      <v-row>
        <v-col class="d-flex justify-center align-center">
          <div class="d-flex flex-column">
            <!-- <h1 style="font-size: 2rem; opacity: 0.3; color: #808080;" v-if="hideContent === false">&#x3c;&#x2215;&#62;
            </h1> -->
            <v-progress-linear v-if="hideContent === false" color="#678EFF" indeterminate
              model-value="100"></v-progress-linear>
            <div class="music-note"> &#x3c;&#x2215;&#62;</div>
            <span class="text-start text-h6 mb-5 font-weight-light animate__animated animate__fadeInLeft">Full Stack
              Developer</span>
            <h1 style="font-size: 10rem!;" class="text-h4 mb-5 animate__animated animate__fadeInLeft animate__delay-1s">
              Hi, I'm <span style="color: #678EFF;">Prajwal</span></h1>
            <v-btn color="#687EFF" width="150"
              class="mb-5 animate__animated animate__fadeInLeft animate__delay-2s">Download
              CV</v-btn>
          </div>
        </v-col>
      </v-row>
      <v-col>
        <v-img src="@/assets/t1.png" width="500" class="animate__animated animate__fadeInRight animate__delay-3s"
          style="background-image: linear-gradient(to bottom, #0040ff, #678EFF); border-radius: 100px 10px; border-bottom: 5px solid #678EFF;"
          cover></v-img>
      </v-col>
    </v-row>
  </v-container>
  <section style="background-color: #131313;" class="pa-16" id="about">
    <v-row class="text-white">
      <v-col>
        <div>
          <v-img style="background-color: #2e2e2e; border-radius: 10%;" height="400" width="400" src="@/assets/i1.jpg">
        </v-img>
        </div>

      </v-col>
      <v-col>
        <h1 class="text-h4 font-weight-bold">About Me</h1>
        <p style="color: rgb(204, 202, 202);">
          I am Prajwal Hanamanthagoudr, a Full Stack Developer with a strong foundation in web development and Java
          programming.
          I have expertise in SQL, JDBC, Hibernate, and web technologies like HTML, CSS, and JavaScript, including
          frameworks like Vue.js.
          With a passion for learning and staying updated with the latest technologies, I am dedicated to delivering
          high-quality solutions.
          I am seeking challenging opportunities to contribute my skills and drive growth in a dynamic organization.</p>
        <v-row class="mt-0 text-subtitle-1 font-weight-black">
          <v-col class="tab relative" :class="{ 'text-blue-500': activeTab === 'skills' }" @click="showSkills">
            Skills
            <v-progress-linear v-if="activeTab === 'skills'" indeterminate color="#678EFF"></v-progress-linear>
          </v-col>
          <v-col class="tab relative" :class="{ 'text-blue-500': activeTab === 'education' }" @click="showEducation">
            Education
            <v-progress-linear v-if="activeTab === 'education'" indeterminate color="#678EFF"></v-progress-linear>
          </v-col>
          <v-col class="tab relative" :class="{ 'text-blue-500': activeTab === 'experience' }" @click="showExperience">
            Experience
            <v-progress-linear v-if="activeTab === 'experience'" indeterminate color="#678EFF"></v-progress-linear>
          </v-col>
          <div class="underline absolute bottom-0 h-1 bg-blue-500 transition-transform"
            :style="{ 'transform': activeTabTransform }"></div>
        </v-row>
        <v-row v-if="activeTab === 'skills'">
          <v-col v-for="(language, index) in languages" :key="index">
            <v-progress-circular :model-value="language.value" :color="language.color" :size="80" :width="8"><span
                style="color:white ;">{{ language.name }}</span></v-progress-circular>
          </v-col>
        </v-row>
        <v-row v-else-if="activeTab === 'education'">
          <v-col>
            <v-container>
              <v-card v-for="info in infos" :key="info.name" class="mb-5"
                style="background-color: #2e2e2e; color: rgb(204, 202, 202);">
                <v-card-title class="text-blue-lighten-1">{{ info.year }}</v-card-title>
                <v-card-text>
                  <div>{{ info.branch === 'SSLC' ? 'Schoole Name' : 'College Name' }}: {{ info.name }}</div>
                  <div>Branch: {{ info.branch }}</div>
                  <div>Percentage: {{ info.per }}</div>
                </v-card-text>
              </v-card>
            </v-container>
          </v-col>
        </v-row>
        <v-row v-else-if="activeTab === 'experience'">
          <v-col>
            <v-card style="background-color: #2e2e2e; color: rgb(204, 202, 202);" class="mb-5" v-for="exps in exp"
              :key="exps.company">
              <v-card-title class="text-blue-lighten-1">{{ exps.year }}</v-card-title>
              <v-card-text>
                <div>Company: {{ exps.company }}</div>
                <div>Role: {{ exps.Role }}</div>
                <div>Duration: {{ exps.duration }}</div>
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>
      </v-col>
    </v-row>
  </section>
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
  data() {
    return {
      hideContent: false,
      activeTab: 'skills',
      languages: [
        { name: 'HTML', value: 88, color: "red" },
        { name: 'CSS', value: 77, color: "blue" },
        { name: 'Js', value: 50, color: "yellow" },
        { name: 'Vue.js', value: 90, color: "green" },
        { name: 'Tailwind', value: 45, color: "blue-lighten-1" },
        { name: 'Git', value: 70, color: "#f34f29" },
        { name: 'Java', value: 65, color: "#f89820" },
        { name: 'Node.js', value: 40, color: "#68a063" },
        { name: 'SQL', value: 65, color: "#00758f" },
        { name: 'Postman', value: 50, color: "#ef5b25 " },
        { name: 'JDBC', value: 75, color: "#00758f" },
        { name: 'Hibernate', value: 60, color: "#37474F" },
      ],
      infos: [
        { name: 'Govt Engineering College Ramanagaram', year: '2018-2022', branch: 'Mechanical Engineering', per: "62%" },
        { name: 'MDRS PU Sience College Savanur', year: '2016-2018', branch: 'PUC Sience', per: "72%" },
        { name: 'MDRS Schoole Negalure', year: '2015-2016', branch: 'SSLC', per: "84%" },
      ],
      exp: [
        { year: '2023', company: 'Infynect Labs Pvt Ltd', Role: 'Full Stack Developer', duration: '5 monts' },
        { year: '2022', company: 'Jspiders Banglore', Role: 'Training Full Stack Development', duration: '5 monts' },
      ]
    }
  },
  mounted() {
    setTimeout(() => {
      this.hideContent = true;
    }, 10000);
  },
  methods: {
    showSkills() {
      this.activeTab = 'skills';
    },
    showEducation() {
      this.activeTab = 'education';
    },
    showExperience() {
      this.activeTab = 'experience';
    },
    scrollToSection(section) {
      const element = document.getElementById(section);
      element.scrollIntoView({ behavior: 'smooth' });
    }
  }
});
</script>

<style>
.music-note {
  font-size: 3rem;
  opacity: 0.3;
  color: #678EFF;
  animation: music-note-animation 2s linear infinite;
}

@keyframes music-note-animation {
  0% {
    transform: rotate(0deg);
  }

  100% {
    transform: rotate(360deg);
  }
}

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
}</style>
