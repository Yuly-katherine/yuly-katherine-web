<template>
  <div class="parallax">
    <div class="container">
      <div class="container-experience">
        <section class="about">
          <div class="about-text">
            <h2 class="about-text__title" id="about">About Me</h2>
            <p class="about-text__description">
              I'm Yuly Katherine Gómez. I consider myself a kind and empathetic
              person, with a strong belief that human warmth is just as
              important as technical skills.
            </p>
            <p class="about-text__description">
              I have 4 years of experience working with Vue.js, using JavaScript
              and various libraries to build intuitive and functional web
              interfaces. Additionally, I’ve also explored other technologies
              like React and TypeScript. While my experience with them is still
              developing, I’m actively working to improve and grow in those
              areas.
            </p>
          </div>
          <div class="about-experience">
            <h2 class="about-experience__title">EDUCATION</h2>
            <div class="about-experience__timeline">
              <el-timeline style="max-width: 600px">
                <el-timeline-item
                  v-for="(element, index) in education"
                  :key="index"
                  :type="element.type"
                  :color="element.color"
                  :size="element.size"
                  :timestamp="element.timestamp"
                >
                  {{ element.content }}
                </el-timeline-item>
              </el-timeline>
            </div>
          </div>
        </section>
        <section id="skills" class="skills">
          <h2 class="skills__title">SKILLS</h2>
          <div class="skills__icons">
            <div>
              <Icon
                class="icon-item"
                icon="vscode-icons:file-type-html"
                width="50"
              />
              <Icon
                class="icon-item"
                icon="skill-icons:css"
                width="50"
                height="50"
              />
              <Icon
                class="icon-item"
                icon="vscode-icons:file-type-scss"
                width="50"
              />
              <Icon class="icon-item" icon="logos:javascript" width="50" />
            </div>
            <div>
              <Icon class="icon-item" icon="logos:vue" width="50" />
              <Icon class="icon-item" icon="logos:pinia" width="50" />
              <Icon class="icon-item" icon="logos:react" width="50" />
              <img
                src="../assets/scss/icons/element-plus-logo.svg"
                width="100"
                height="50"
              />
            </div>
          </div>
        </section>
      </div>
    </div>
  </div>
</template>

<script setup>
//----------IMPORTS----------//
import { Icon } from "@iconify/vue";
import { ref } from "vue";
//----------VARIABLES----------//
const education = ref([
  {
    content: "Electrical Engineering Degree",
    timestamp: "Dec. 2016 - Antioquia University",
    color: "#075f45",
    size: "large",
  },
  {
    content: "Course Vue.Js",
    timestamp: "Apr.2021 - Platzi",
    color: "#075f45",
    size: "large",
  },
  {
    content: "Web Developer",
    timestamp: "Aug. 2022 - Coderhouse (Top 10 best students)",
    color: "#075f45",
    size: "large",
  },
  {
    content: "Course JavaScript",
    timestamp: "Apr.2022 - Coderhouse (Top 10 best students)",
    color: "#075f45",
    size: "large",
  },
  {
    content: "Course React.Js",
    timestamp: "Dic. 2022 - Coderhouse (Top 10 best students)",
    color: "#075f45",
    size: "large",
  },
]);
</script>

<style lang="scss"scoped>
.container {
  background-color: $color-white;
  width: 80%;
  height: auto;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  align-items: center;
  max-width: 1400px;
}
.container-experience {
  background-color: $color-white;
  text-align: center;
  margin: 0px auto;
  height: 900px;
  width: 100%;
  border: 20px solid $color-white;
  border-radius: 10px;
}

.about {
  display: grid;
  grid-template-columns: 1fr 1fr;
  padding: 20px 10px;
}
.about-text {
  display: flex;
  flex-direction: column;
  align-items: center;
  &__title {
    @include general-title(5.0em);
    margin: 0;
  }
  &__description {
    text-align: left;
    width: 450px;
    font-size: 1.2em;
  }
}

.about-experience {
  display: flex;
  flex-direction: column;
  align-items: center;
  &__title {
    @include general-title(5.0em);
    margin: 0;
  }
  &__timeline {
    padding-top: 1em;
    height: 400px;
    max-width: 600px;
  }
}

:deep(.el-timeline-item__wrapper) {
  padding-top: 0.2em;
  text-align: left;
  font-size: 1.2em;
}

:deep(.el-timeline-item__timestamp) {
  font-size: 1em;
}
.skills {
  display: flex;
  align-items: center;
  justify-content: space-evenly;
  padding: 10px 0;
  &__title {
    @include general-title(5.0em);
    margin: 0;
  }
  &__icons {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
}

.icon-item {
  margin: 10px 20px;
}

.parallax {
  position: relative;
  min-height: 900px;
  overflow: hidden;
}
.parallax::before {
  content: "";
  position: absolute;
  left: 0;
  width: 100%;
  height: 100%;
  background-image: url("../../public/landscape.jpg"); 
  background-attachment: fixed;
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
  opacity: 0.2;
  z-index: 1;
}

</style>