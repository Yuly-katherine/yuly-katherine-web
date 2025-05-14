<template>
  <div class=" container-general">
    <div class="container-projects">
    <section class="projects" id="projects">
      <h2 class="projects__title">Projects</h2>
      <div class="projects__cards">
        <div class="card-element" v-for="card of cards" :key="card.name">
          <el-card style="max-width: 320px; max-height: 600px">

            <div class="image-container">
              <img
                class="image"
                :src="card.img"
                :alt="card.alt"
              />
              <div class="overlay">
                <a :href="card.github" target="_blank">
                  <Icon icon="mdi:github" width="40" height="40" />
                </a>
                <a :href="card.link" target="_blank">
                  <Icon icon="mdi:link-variant" width="40" height="40" />
                </a>
              </div>
            </div>
            <template #footer>{{ card.description }}</template>
          </el-card>
        </div>
      </div>
    </section>
  </div>
  </div>
</template>

<script  setup>
//----------IMPORTS----------//
import { Icon } from "@iconify/vue";
import { ref } from "vue";

//----------VARIABLES----------//
const cards = ref([
  {
    name: "BurgerEcommerce",
    description:
      "Burger Chips is a hamburger store built with React that allows users to view the full menu, and add products to a shopping cart. The application enables real-time cart management, offering a smooth and interactive experience. All data —such as products— is stored and managed using Firebase.",
    img: "burgerChips.png",
    alt:"BurgerEcommerce",
    github:"https://github.com/Yuly-katherine/Burguer-Eccomerce",
    link: "https://yuly-katherine.github.io/Burguer-Eccomerce/"
  },
  {
    name: "favoritePokemon",
    description:
      "Pokedex is a web app built with Vue that allows users to explore a list of Pokémon, view detailed information for each, and mark their favorites. It includes a filter to display only favorite Pokémon, enhancing user interaction. The project also integrates Vitest for unit testing, ensuring reliable and maintainable code.",
    img: "pokedex.png",
    alt:"favoritePokemon",
    github:"https://github.com/Yuly-katherine/pokedex-app",
    link: "https://yuly-katherine.github.io/pokedex-app/"
  },
]);
</script>

<style lang="scss" scoped>
.container-general {
  background-color: $color-white;
  width: 80%;
  height: auto;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  align-items: center;
  max-width: 1400px;
}

.container-projects {
  background-color: $color-background-primary;
  text-align: center;
  margin: 0px auto;
  height: 900px;
  width: 100%;
  border: 20px solid $color-white;
  border-radius: 10px;
}

.projects {
  display: flex;
  flex-direction: column;
  padding: 10px;
  &__title {
    @include general-title(5.5em);
    margin: 0;
  }
  &__cards {
    display: flex;
    flex-wrap: wrap;
  }
}

.card-element {
  padding: 1em;
}


.image-container {
  position: relative;
  overflow: hidden;
}

.image {
  width: 100%;
  height: 300px;
  display: block;
  transition: transform 0.3s ease;
}

.image-container:hover .image {
  transform: scale(1.05);
}

.overlay {
  position: absolute;
  top: 0;
  left: 0;
  height: 100%;
  width: 100%;
  background-color: rgba(0, 0, 0, 0.5); /* Oscurece imagen */
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 20px;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.image-container:hover .overlay {
  opacity: 1;
}

.overlay a {
  color: white;
  transition: transform 0.3s ease;
}

.overlay a:hover {
  transform: scale(1.2);
}
</style>