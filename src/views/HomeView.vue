<template>
  <NavigationBar @scrollToSection="scrollToSection" />
  <v-container class="text-center" id="home">
    <v-row class="text-white">
      <v-row>
        <v-col class="d-flex justify-center align-center">
          <div class="d-flex flex-column">
            <v-progress-linear
              v-if="hideContent === false"
              color="#678EFF"
              indeterminate
            ></v-progress-linear>
            <v-icon class="music-note ml-16">mdi-xml</v-icon>
            <span
              class="text-start text-h6 mb-5 font-weight-light animate__animated animate__fadeInLeft"
              >Full Stack Developer</span
            >
            <h1
              style="font-size: 10rem!"
              class="text-h3 mb-5 animate__animated animate__fadeInLeft animate__delay-1s"
            >
              Hi, I'm <span style="color: #678eff">Prajwal</span>
            </h1>
            <v-btn
              color="#687EFF"
              width="150"
              class="mb-5 animate__animated animate__fadeInLeft animate__delay-2s"
              @click="download"
              >Download CV</v-btn
            >
          </div>
        </v-col>
      </v-row>
      <v-col>
        <v-img
          src="@/assets/t1.png"
          width="500"
          class="animate__animated animate__fadeInRight animate__delay-3s"
          style="
            background-image: linear-gradient(to bottom, #0040ff, #678eff);
            border-radius: 100px 10px;
            border-bottom: 5px solid #678eff;
          "
          cover
        ></v-img>
      </v-col>
    </v-row>
  </v-container>
  <section style="background-color: #131313" class="pa-16" id="about">
    <v-row class="text-white">
      <v-col>
        <div>
          <v-img
            style="background-color: #2e2e2e; border-radius: 10%"
            height="400"
            width="400"
            src="@/assets/i1.jpg"
          >
          </v-img>
        </div>
      </v-col>
      <v-col>
        <h1 class="text-h3 font-weight-bold mb-5">About Me</h1>
        <p style="color: rgb(204, 202, 202)" class="text-justify">
          I am Prajwal Hanamanthagoudr, a Full Stack Developer with a strong foundation in
          web development and Java programming. I have expertise in SQL, JDBC, Hibernate,
          and web technologies like HTML, CSS, and JavaScript, including frameworks like
          Vue.js. With a passion for learning and staying updated with the latest
          technologies, I am dedicated to delivering high-quality solutions. I am seeking
          challenging opportunities to contribute my skills and drive growth in a dynamic
          organization.
        </p>
        <v-row class="mt-0 text-subtitle-1 font-weight-black" style="cursor: pointer;">
          <v-col class="tab relative" @click="showSkills"> 
            Skills
            <v-progress-linear
              v-if="activeTab === 'skills'"
              model-value="100"
              color="#678EFF"
            ></v-progress-linear>
          </v-col>
          <v-col class="tab relative" @click="showEducation">
            Education
            <v-progress-linear
              v-if="activeTab === 'education'"
              model-value="100"
              color="#678EFF"
            ></v-progress-linear>
          </v-col>
          <v-col class="tab relative" @click="showExperience">
            Experience
            <v-progress-linear
              v-if="activeTab === 'experience'"
              model-value="100"
              color="#678EFF"
            ></v-progress-linear>
          </v-col>
          <div
            class="underline absolute bottom-0 h-1 bg-blue-500 transition-transform"
            :style="{ transform: activeTabTransform }"
          ></div>
        </v-row>
        <v-row v-if="activeTab === 'skills'">
          <v-col v-for="(language, index) in languages" :key="index">
            <v-progress-circular
              :model-value="language.value"
              :color="language.color"
              :size="80"
              :width="8"
              ><span style="color: white">{{ language.name }}</span></v-progress-circular
            >
          </v-col>
        </v-row>
        <v-row v-else-if="activeTab === 'education'">
          <v-col>
            <v-container>
              <v-card
                v-for="info in infos"
                :key="info.name"
                class="mb-5"
                style="background-color: #2e2e2e; color: rgb(204, 202, 202)"
              >
                <v-card-title class="text-blue-lighten-1">{{ info.year }}</v-card-title>
                <v-card-text>
                  <div>
                    {{ info.branch === "SSLC" ? "Schoole Name" : "College Name" }}:
                    {{ info.name }}
                  </div>
                  <div>Branch: {{ info.branch }}</div>
                  <div>Percentage: {{ info.per }}</div>
                </v-card-text>
              </v-card>
            </v-container>
          </v-col>
        </v-row>
        <v-row v-else-if="activeTab === 'experience'">
          <v-col>
            <v-card
              style="background-color: #2e2e2e; color: rgb(204, 202, 202)"
              class="mb-5"
              v-for="exps in exp"
              :key="exps.company"
            >
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
  <v-container id="services" class="mt-16">
    <h1 class="text-h3 font-weight-bold text-white mb-10 ml-10">My Services</h1>
    <v-row>
      <v-col v-for="card in cards" :key="card.title">
        <v-card
          class="mx-auto"
          width="300"
          color="#2e2e2e"
          @mouseover="card.hover = true"
          @mouseleave="card.hover = false"
          :class="{ 'scale-effect': card.hover }"
        >
          <v-icon class="ml-5 text-white text-h4 mt-5">{{ card.icon }}</v-icon>
          <v-card-title class="font-weight-bold text-white">{{
            card.title
          }}</v-card-title>
          <v-card-text class="text-white">
            <div>{{ card.content }}</div>
          </v-card-text>
          <v-card-actions>
            <v-btn variant="text" :href="card.website" target="_blank" color="blue">
              Learn More
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
  <v-container id="portfolio" class="mt-16">
    <h1 class="text-h3 font-weight-bold text-white mb-10 ml-10">My Work</h1>
    <v-row>
      <v-col v-for="(image, index) in images" :key="index" class="text-center">
        <v-card class="mx-auto pa-1 rounded-xl" width="350" height="400" color="#2e2e2e">
          <v-img :src="image.src" class="bg-grey-lighten-2 rounded-xl" height="300">
          </v-img>
          <v-card-title class="text-white">
            {{ image.title }}
          </v-card-title>
          <v-card-actions gradient="to bottom, #2980B9, #6DD5FA">
            <v-btn
              color="blue"
              :href="image.website"
              target="_blank"
              append-icon="mdi-arrow-right"
            >
              Explore
            </v-btn>
            <v-spacer></v-spacer>
            <v-btn
              density="comfortable"
              :href="image.website"
              target="_blank"
              icon="mdi-open-in-new"
              color="blue"
              elevation="24"
            ></v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
    <v-row>
      <v-btn
        class="d-flex mx-auto text-white mt-8 font-weight-bold text-capitalize"
        href="https://github.com/PrajwalHanamanthagoudr?tab=repositories"
        target="_blank"
        style="background-color: #2e2e2e; border: 2px solid #678eff"
        >See more</v-btn
      >
    </v-row>
  </v-container>
  <v-container id="contact" class="mt-16">
    <v-row>
      <v-col>
        <h1 class="text-h3 font-weight-bold text-white mb-4 ml-4">Contact Me</h1>
        <v-btn
          class="text-lowercase text-white"
          flat
          prepend-icon="mdi-gmail"
          href="https://mail.google.com/mail/u/0/#inbox?compose=new"
          target="_blank"
          variant="text"
        >
          <template v-slot:prepend> <v-icon color="blue"></v-icon> </template
          >prajwalhanamanthagoudr@gmail.com</v-btn
        ><br />
        <v-btn
          class="text-lowercase text-white"
          flat
          prepend-icon="mdi-phone"
          variant="text"
        >
          <template v-slot:prepend> <v-icon color="blue"></v-icon> </template>+91
          6361237206</v-btn
        >
        <v-row>
          <v-col v-for="icon in icons" :key="icon">
            <v-btn
              :icon="icon.name"
              elevation="24"
              variant="text"
              color="#678EFF"
              :href="icon.link"
              target="_blank"
            ></v-btn>
          </v-col>
        </v-row>
        <v-btn color="#687EFF" width="150" class="mt-5 text-white" @click="download"
          >Download CV</v-btn
        >
      </v-col>
      <v-col style="color: lightgray">
        <v-text-field
          color="blue"
          label="Your Name*"
          v-model="username"
          bg-color="#2e2e2e"
          required
        ></v-text-field>
        <v-text-field
          color="blue"
          label="Your Email*"
          v-model="email"
          bg-color="#2e2e2e"
          required
        ></v-text-field>
        <v-textarea
          color="blue"
          label="Your Message*"
          v-model="message"
          bg-color="#2e2e2e"
          required
        ></v-textarea>
        <v-btn
          color="#678EFF"
          class="pl-5 pr-5 font-weight-bold text-capitalize"
          @click="submit"
          >Submit</v-btn
        >
        <v-snackbar v-model="snackbar" location="bottom" :color="color">
          {{ text }}

          <template v-slot:actions>
            <v-btn color="black" variant="text" @click="snackbar = false"> Close </v-btn>
          </template>
        </v-snackbar>
      </v-col>
    </v-row>
  </v-container>
  <section style="background-color: #2e2e2e">
    <v-container>
      <h4 class="text-center text-white">
        Copyright <v-icon>mdi-copyright</v-icon> Made by Prajwal Hanamanthagoudr
        <v-icon color="red">mdi-heart</v-icon>
      </h4>
    </v-container>
  </section>
  <ModalPage />
</template>

<script>
import { defineComponent } from "vue";

// Components
import NavigationBar from "@/components/NavigationBar.vue";
import ModalPage from "@/components/ModalPage.vue";

export default defineComponent({
  name: "HomeView",
  components: {
    NavigationBar,
    ModalPage,
  },
  data() {
    return {
      username: "",
      email: "",
      message: "",
      hideContent: false,
      activeTab: "skills",
      languages: [
        { name: "HTML", value: 95, color: "red" },
        { name: "CSS", value: 77, color: "blue" },
        { name: "Js", value: 50, color: "yellow" },
        { name: "Vue.js", value: 90, color: "green" },
        { name: "Tailwind", value: 45, color: "blue-lighten-1" },
        { name: "Git", value: 70, color: "#f34f29" },
        { name: "Java", value: 65, color: "#f89820" },
        { name: "Node.js", value: 40, color: "#68a063" },
        { name: "SQL", value: 65, color: "#00758f" },
        { name: "Postman", value: 60, color: "#ef5b25 " },
        { name: "JDBC", value: 75, color: "#00758f" },
        { name: "Hibernate", value: 60, color: "#37474F" },
      ],
      infos: [
        {
          name: "Govt Engineering College Ramanagaram",
          year: "2018-2022",
          branch: "Mechanical Engineering",
          per: "62%",
        },
        {
          name: "MDRS PU Sience College Savanur",
          year: "2016-2018",
          branch: "PUC Sience",
          per: "72%",
        },
        { name: "MDRS Schoole Negalure", year: "2015-2016", branch: "SSLC", per: "84%" },
      ],
      exp: [
        {
          year: "2023",
          company: "Infynect Labs Pvt Ltd",
          Role: "Full Stack Developer",
          duration: "5 monts",
        },
        {
          year: "2022",
          company: "Jspiders Banglore",
          Role: "Training Full Stack Development",
          duration: "5 monts",
        },
      ],
      cards: [
        {
          title: "Web Design",
          icon: "mdi-laptop",
          content:
            "I specialize in creating visually appealing and user-friendly web interfaces using HTML, CSS, JavaScript.",
          website: " https://prajwalhanamanthagoudr.github.io/photography/",
          hover: false,
        },
        {
          title: "Backend Development",
          icon: "mdi-server",
          content:
            "I focus on building robust and scalable server-side applications using languages like Python, Java, and Node.js.",
          website: "https://prajwalhanamanthagoudr.github.io/Job-portal/",
          hover: false,
        },
        {
          title: "Web Development Backend Support",
          icon: "mdi-cogs",
          content:
            "I provide backend support for web development projects, troubleshooting issues and optimizing performance.",
          website: "https://prajwalhanamanthagoudr.github.io/portfolio/",
          hover: false,
        },
      ],
      images: [
        {
          src: require("../assets/m5.png"),
          title: "Photographer Website",
          website: " https://prajwalhanamanthagoudr.github.io/photography/",
        },
        {
          src: require("../assets/m4.png"),
          title: "Job Posting Website",
          website: "https://prajwalhanamanthagoudr.github.io/Job-portal/",
        },
        {
          src: require("../assets/m3.png"),
          title: "Portfolio Website",
          website: "https://prajwalhanamanthagoudr.github.io/portfolio/",
        },
      ],
      icons: [
        {
          link: "#",
          name: "mdi-facebook",
        },
        {
          link: "#",
          name: "mdi-instagram",
        },
        {
          link: "https://github.com/PrajwalHanamanthagoudr?tab=repositories",
          name: "mdi-github",
        },
        {
          link: "#",
          name: "mdi-telegram",
        },
        {
          link: "www.linkedin.com/in/prajwal-hanamanthagoudr-789588242",
          name: "mdi-linkedin",
        },
      ],
      snackbar: false,
      text: "",
      color: "",
      scriptURL: 'https://script.google.com/macros/s/AKfycbwaRsz-u4TeaHl7F1O-2LHe1ZI6hDtovmrtteB_KDnxPjscBOMh0lqUCmNJVG86Jscuzg/exec',
    };
  },
  mounted() {
    setTimeout(() => {
      this.hideContent = true;
    }, 10000);
  },
  methods: {
    showSkills() {
      this.activeTab = "skills";
    },
    showEducation() {
      this.activeTab = "education";
    },
    showExperience() {
      this.activeTab = "experience";
    },
    scrollToSection(section) {
      const element = document.getElementById(section);
      element.scrollIntoView({ behavior: "smooth" });
    },
    download() {
      const link = document.createElement("a");
      link.href = "@/assets/r1.pdf";
      link.download = "resume.pdf";
      link.click();
    },
    submit() {
      if (!this.username || !this.email || !this.message) {
        this.color = "red";
        this.snackbar = true;
        this.text = "Enter required fields...!";
      } else {
        const isValidEmail = /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(this.email);
        if (!isValidEmail) {
          this.color = "red";
          this.snackbar = true;
          this.text = "Invalid email address...!";
        } else {
          const formData = new FormData();
          formData.append('username', this.username);
          formData.append('email', this.email);
          formData.append('message', this.message);
          
          fetch(this.scriptURL, {
            method: 'POST',
            body: formData
          })
          .then(response => {
            console.log("Thank you! Your form is submitted successfully."+response);
            this.color = "green";
            this.snackbar = true;
            this.text = "Successfully submitted...!";
            this.username = ""
            this.email = ""
            this.message = ""
          }).catch(error => console.error('Error!', error.message))
        }
      }
    },
    
    
  },
});
</script>

<style>
.music-note {
  font-size: 6rem;
  opacity: 0.3;
  color: #678eff;
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
}

.scale-effect {
  transform: scale(1.05);
  transition: transform 0.3s;
}

.scale-effect:hover {
  background-image: linear-gradient(
    to left bottom,
    #8c00dc,
    #c600ba,
    #e80096,
    #f90074,
    #ff0057
  );
}
</style>
