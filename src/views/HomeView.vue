<template>
  <div class="home">
    <div class="container-fluid">
      <div class="row">
        <div v-if="isRTL" class="col-md-9 order-md-2">
          <img alt="logo" src="../assets/co2.png" style="max-width: 100%; margin-top: 10px; margin-bottom: 10px;">
          <Co2Table />
        </div>
        <div v-else class="col-md-9">
          <img alt="logo" src="../assets/co2.png">
          <Co2Table />
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
import Co2Table from '@/components/Co2Table.vue'
import LocalLinks from '@/components/LocalLinks.vue'

export default {
  name: 'HomeView',
  components: {
    Co2Table,
    LocalLinks,
  },
  computed: {
    isRTL() {
      const lang = navigator.language;
      if (lang === "ar" || lang === "he" || lang === "fa" || lang === "ur") {
        return false; // is not right-to-left
      } else {
        return true; // is right-to-left
      }
    },
  },
}
</script>
