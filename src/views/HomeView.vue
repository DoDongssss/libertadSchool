<template>
  <loader :isLoading="loading" />
  <div :class="loading ? 'hidden' : ''">
    <div class="relative z-10 h-full w-full bg-white">
      <headerView :activeSection="activeSection" />
      <mainSection id="home" />
      <div class="relative">
        <taglineBox />
      </div>
      <div
        class="flex flex-col gap-[150px] p-[100px] px-[25px] sm:px-[50px] lg:px-[150px]"
      >
        <aboutSection id="about" />
        <competenciesSection />
        <!-- <educationSection id="education" /> -->
        <ourCampusSection id="campus" />
        <affiliationSection id="affiliation" />
        <contactusSection id="contact" />
      </div>
      <footer class="mb-[800px] bg-[#111]"></footer>
      <!-- back to top button -->
      <el-backtop :right="50" :bottom="80" :size="500" />
    </div>
    <footerView />
  </div>
</template>

<script>
import { ref } from "vue";
import headerView from "../components/header.vue";
import footerView from "../components/footer.vue";
import mainSection from "../components/mainSection.vue";
import taglineBox from "../components/taglineBox.vue";
import aboutSection from "../components/mainSection.vue";
import competenciesSection from "../components/mainSection.vue";
import educationSection from "../components/educationSection.vue";
import ourCampusSection from "../components/ourCampusSection.vue";
import affiliationSection from "../components/fifthSection.vue";
import contactusSection from "../components/fifthSection.vue";
import loader from "../components/loader.vue";

export default {
  components: {
    mainSection,
    headerView,
    footerView,
    taglineBox,
    aboutSection,
    competenciesSection,
    educationSection,
    ourCampusSection,
    affiliationSection,
    contactusSection,
    loader,
  },
  setup() {
    const loading = ref(true);
    const educationPos = ref(null);
    const activeSection = ref("home");

    return {
      loading,
      educationPos,
      activeSection,
    };
  },
  methods: {
    loaderHandler() {
      this.loading = false;
    },
    checkVisibleSection() {
      const sections = [
        "home",
        "about",
        "education",
        "campus",
        "affiliation",
        "contact",
      ];

      for (const section of sections) {
        const element = document.getElementById(section);
        if (element) {
          const rect = element.getBoundingClientRect();
          if (
            rect.top <= window.innerHeight / 2 &&
            rect.bottom >= window.innerHeight / 2
          ) {
            this.activeSection = section;
            console.log(this.activeSection);
            break;
          }
        }
      }
    },
  },
  mounted() {
    // setTimeout(() => {
    //    this.loading = false
    //    console.log("yes")
    // }, 10000)
    window.addEventListener("load", this.loaderHandler);

    window.addEventListener("scroll", this.checkVisibleSection);
  },
};
</script>

<style lang="scss" scoped></style>
