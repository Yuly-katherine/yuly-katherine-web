<template>
  <div class="container">
      <div class="container-profile">
    <header class="header-profile">
      <div class="header-profile__name">Yuly K.</div>
      <nav class="header-profile__menu">
        <a class="header-profile__menu-item" href="#about">About</a>
        <a class="header-profile__menu-item" href="#skills">Skills</a>
        <a class="header-profile__menu-item" href="#projects">Projects</a>
        <a class="header-profile__menu-item" href="#contact">Contact</a>
      </nav>
      <nav class="header-profile__social">
        <a href="https://www.linkedin.com/in/yulykgomezv/" target="_blanck"
          ><Icon
            class="icon-item"
            icon="akar-icons:linkedin-fill"
            width="30"
            height="30"
          />
        </a>
        <a
          href="https://github.com/Yuly-katherine"
          target="_blanck"
          class="header-profile__social-item"
          ><Icon class="icon-item" icon="logos:github-icon" width="30"
        /></a>
      </nav>
    </header>
    <section class="img-profile">
      <p class="img-profile__text-introduce">HI THERE, I'M YULY</p>
      <img src="../../public/Me.png" alt="Yuly" class="img-profile__img" />
      <div class="img-profile__text">
        <h1 class="frontend-left">FRONT</h1>
        <h1 class="frontend-right">END</h1>
        <h1 class="developer-left">DEVELOPER</h1>
        <h1 class="developer-right">&lt;/&gt;</h1>
      </div>
      <p class="img-profile__text-msj">
        I enjoy creating digital experiences that feel as good as they look — intuitive, beautiful, and designed to connect with people on every click.
      </p>
    </section>
  </div>
  </div>
</template>

<script setup>
//---------IMPORTS----------//
import { Icon } from "@iconify/vue";
</script>

<style lang="scss" scoped>
.container {
  background-color: $color-white;
  width: 80%;
  height: auto;
  margin: 0 auto;
  margin-top: 5rem;
  border-radius: 10px;
  display: flex;
  flex-direction: column;
  align-items: center;
  max-width: 1400px;
}
.container-profile {
  background-color: $color-background-primary;
  text-align: center;
  margin: 0px auto;
  height: 100vh;
  width: 100%;
  border: 20px solid $color-white;
  border-radius: 10px;
}

.header-profile {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding-top: 40px;
  &__name {
    font-family: "Dancing Script", cursive;
    font-size: 3em;
    font-weight: bold;
    margin-left: 1em;
  }
  &__menu {
    background-color: $color-white;
    border-radius: 25px;
    padding: 1.5em;
  }
  &__menu-item {
    margin: 0 20px;
    font-size: 1.5em;
    &:hover {
      opacity: 0.7;
    }
  }
  &__social {
    display: flex;
    align-items: center;
    margin-right: 30px;
  }
  &__social-item {
    margin-right: 1em;
  }
}

.icon-item {
  margin: 10px 15px;
  &:hover {
    opacity: 0.7;
  }
}

.img-profile {
  font-family: "Bebas Neue", sans-serif;
  position: relative;
  height: 100vh;
  overflow: hidden;
  &__text-introduce {
    padding-top: 0.5em;
    font-size: 3em;
    font-weight: 100;
  }
  &__img {
    position: absolute;
    bottom: 0;
    left: 50%;
    transform: translate(-50%, -50%);
    max-width: 100vw;
    max-height: 100vh;
    width: 55%;
    height: 55%;
    object-fit: contain;
    z-index: 200;
  }
  &__text {
    @include general-title(5.5em);
  }
  &__text-msj {
    font-family: "VT323", monospace;
    font-size: 1.3em;
    position: absolute;
    top: 40%;
    right: 2%;
    width: 200px;
    text-align: left;
    z-index: 100;
  }
}

.frontend-left {
  position: absolute;
  top: 30%;
  left: 35%;
  transform: translate(-50%, -50%);
  z-index: 300;
  margin: 0;
}

.frontend-right {
  position: absolute;
  top: 30%;
  left: 65%;
  transform: translate(-50%, -50%);
  z-index: 100;
  margin: 0;
}

.developer-left {
  position: absolute;
  top: 62%;
  left: 37%;
  transform: translate(-50%, -50%);
  z-index: 300;
  margin: 0;
}

.developer-right {
  position: absolute;
  top: 62%;
  left: 65%;
  transform: translate(-50%, -50%);
  z-index: 300;
  margin: 0;
}
</style>