<script setup>
import { RouterLink, RouterView } from 'vue-router'

import {ref} from 'vue';

const anim =ref('fade');
</script>

<template>
 
      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>

      <div class="check">
        <label>
          <input type="radio" name="anim" value="fade" v-model="anim">Fade
        </label>
        <label>
          <input type="radio" name="anim" value="slide" v-model="anim">Slide
        </label>
        <label>
          <input type="radio" name="anim" value="slide-down" v-model="anim">Slide-Down
        </label>
        <label>
          <input type="radio" name="anim" value="grow-in" v-model="anim">Grow-In
        </label>
        <label>
          <input type="radio" name="anim" value="grow-out" v-model="anim">Grow-Out
        </label>
      </div>
   

  <RouterView v-slot="{Component}">
              <transition :name="anim" mode="out-in">
                <Component :is="Component" />
              </transition>
  </RouterView>
</template>

<style>
*{
  margin:0;
  padding:0;
  box-sizing: border-box;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

nav{
  display: flex;
  align-items: center;
  justify-content: center;
  padding:1rem;
}

nav a{
  margin:0 0.5rem;
  color:black;
  text-decoration: none;
}

.check{
  display: flex;
  justify-content: center;
  align-items: center;
}

.check label{
  margin:0 0.5rem;
}

nav a:hover,
nav a.router-link-exact-active{
  color: crimson;
  text-decoration: underline;
}

main{
  padding:1rem;
  max-width: 768px;
  margin:0 auto;
  will-change: transform, opacity;
}

h1{
  margin-bottom: 1.5rem;
}

p{
  margin-bottom: 1rem;
}

img{
  width:100%;
  max-width: 100%;
  margin-bottom:1.5rem;
}

.fade-enter-from,
.fade-leave-to{
  opacity:0;
}

.fade-enter-active,
.fade-leave-active{
transition: opacity .3s ease-out;
}

.slide-enter-from,
.slide-leave-to {
	opacity: 0;
	transform: translateX(-100%);
}
.slide-enter-active,
.slide-leave-active {
	transition: 0.3s ease-out;
}
.slide-down-enter-from,
.slide-down-leave-to {
	opacity: 0;
	transform: translateY(300px);
}
.slide-down-enter-active,
.slide-down-leave-active {
	transition: 0.3s ease-out;
}
.grow-in-enter-from,
.grow-in-leave-to {
	opacity: 0;
	transform: scale(0.3);
}
.grow-in-enter-active,
.grow-in-leave-active {
	transition: 0.3s ease-out;
}
.grow-out-enter-from,
.grow-out-leave-to {
	opacity: 0;
	transform: scale(1.5);
}
.grow-out-enter-active,
.grow-out-leave-active {
	transition: 0.3s ease-out;
}

</style>
