<template>
    <v-layout>
      <v-navigation-drawer
        v-model="drawer"
        temporary
      >
        <v-list-item
          prepend-avatar="https://randomuser.me/api/portraits/men/78.jpg"
          title="John Leider"
        ></v-list-item>

        <v-divider></v-divider>

        <v-list density="compact" nav>
          <v-list-item prepend-icon="mdi-view-dashboard" title="Home" value="home"></v-list-item>
          <v-list-item prepend-icon="mdi-forum" title="About" value="about"></v-list-item>
        </v-list>
      </v-navigation-drawer>
      <v-main style="height: 250px">
        <div class="d-flex justify-center align-center h-100">
          <v-btn
            id="icon"
            class="far fa-bars"
            color="black"
            @click.stop="drawer = !drawer"
          >
          </v-btn>
        </div>
      </v-main>
    </v-layout>
</template>

<script>
  export default {
    data () {
      return {
        drawer: null,
        
      }
    },
  }
</script>

<style>
#icon {
    display: flex;
    align-items: center;
    position: absolute;
    top: 6px;
    right: 24px;
    font-size: 24px;
    transition: .8 ease all;
    z-index: 999;
}
</style>