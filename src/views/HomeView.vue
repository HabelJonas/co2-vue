<!-- <template>
  <div class="home">
    <div class="container-fluid">
      <div class="row">
        <div class="col-md-9">
          <img alt="Vue logo" src="../assets/co2.png">
          <HelloWorld msg="Welcome to Your Vue.js App" />
        </div>
      </div>
    </div>

  </div>
</template> -->

<template>
  <div class="home">
    <div class="container-fluid">
      <div class="row">
        <div v-if="isRTL" class="col-md-9 order-md-2">
          <img alt="Vue logo" src="../assets/co2.png">
          <HelloWorld msg="Welcome to Your Vue.js App" />
        </div>
        <div v-else class="col-md-9">
          <img alt="Vue logo" src="../assets/co2.png">
          <HelloWorld msg="Welcome to Your Vue.js App" />
        </div>
        <div v-if="isRTL" class="col-md-3">
          <LocalLinks />
        </div>
        <div v-else class="col-md-3 order-md-2">
          <LocalLinks />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import LocalLinks from '@/components/LocalLinks.vue'

export default {
  name: 'HomeView',
  components: {
    HelloWorld,
    LocalLinks,
  },
  computed: {
    isRTL() {
      const lang = navigator.language;
      if (lang === "ar" || lang === "he" || lang === "fa" || lang === "ur") {
        return false;
      } else {
        return true;
      }
    },
  },
}
</script>
