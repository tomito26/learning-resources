<template>
  <div>
    <learning-resource
      v-for="resource in resources"
      :key="resource.id"
      :id="resource.id"
      :title="resource.title"
      :description="resource.description"
      :link="resource.link"
    
    ></learning-resource>
  </div>
</template>

<script>
import LearningResource from "./LearningResource.vue";

export default {
  components: {
    LearningResource,
  },
  inject: {
    resources: {
      type: Object,
      required: true,
    },
   
  },
 
};
</script>

<style scoped>
div {
  max-width: 40rem;
  margin: 3rem auto;
}
</style>