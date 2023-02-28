<template>
  <the-header></the-header>
  <the-resources></the-resources>
</template>

 <script>
import TheHeader from "./components/layouts/TheHeader.vue";
import TheResources from "./components/learn-resources/TheResources.vue";
export default {
  components: {
    TheHeader,
    TheResources,
  },
};
</script>

 <style>
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@400;500;700&display=swap");
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: "Roboto", sans-serif;
}
</style>