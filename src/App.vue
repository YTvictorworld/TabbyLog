<script>
import { RouterLink, RouterView } from 'vue-router'
import navbar from './components/Base/Navbar.vue';
import MobileNav from './components/Base/MobileNav.vue'
export default {
  name: "App",
  components: {
  navbar,
  MobileNav
  }, 

  data () {
      return {
        mobile: null,
        winWidth: null,
      }
    },

  mounted() {
    window.addEventListener('resize', this.checkScreen);

  },

  methods: {
    checkScreen() {
     this.winWidth = this.$vuetify.display.width;
     if(this.winWidth <= 830) {
                this.mobile = true;
                return;
            }
            this.mobile = false;
          }
  }
}
</script>

<template>
  <navbar />
  <MobileNav v-show="mobile" />
<!--   <RouterView /> -->
</template>

