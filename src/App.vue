<template>
  <div v-if="platform === 'web'">
    <jeep-sqlite />
  </div>
  <router-view />
</template>
<script>
import { defineComponent,/* getCurrentInstance,*/ onMounted } from "vue";
import { useSQLite } from "vue-sqlite-hook/dist";
import { Capacitor } from '@capacitor/core';

export default defineComponent({
  name: "App",
  setup() {
//    const app = getCurrentInstance();
    const platform = Capacitor.getPlatform();

    onMounted(async () => {
      console.log("APP.vue");
      console.log("uu", useSQLite({}));
    });
    return {platform};
  }
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
