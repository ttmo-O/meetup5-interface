<script setup lang="ts">
import { RouterLink, RouterView } from "vue-router";
import HelloWorld from "./components/HelloWorld.vue";
import Dwitter from "./components/Dwitter.vue";
</script>

<template>
  <header>
    <Dwitter></Dwitter>

    <!-- <div class="wrapper"> -->
    <div class="column">
      <div class="row">
        <img
          id="logo"
          alt="logo"
          class="logo"
          src="@/assets/ttmo.png"
          width="500"
        />
        
        <div class="wrapper" id="isim">
          <HelloWorld msg="Türkiye Tersine Mühendisler Odası" body="meetup #5" />
    
          <!-- <nav>
            <RouterLink to="/">Home</RouterLink>
            <RouterLink to="/about">About</RouterLink>
          </nav> -->
        </div>
      </div>
  
      <div class="sponsortext">
        Sponsor:
        <img
          id="sponsor"
          alt="sponsor"
          src="@/assets/malwation.png"
          width="600"
        />
      </div>
    </div>
    <!-- </div> -->

  </header>

  <RouterView />
</template>

<style scoped>
#isim {
  margin-top: 5rem;
}
.row {
  display: flex;
  place-items: center;
  /* flex-wrap: wrap; */
}

.column {
  display: block;
}
.sponsortext {
  padding-top: 2em;
  display: grid;
  /* padding-left: 1em; */
  /* margin: 1em; */
}

#sponsor {
  margin-top: 0.5em;
}

header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 5rem 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
