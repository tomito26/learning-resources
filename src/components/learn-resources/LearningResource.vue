<template>
  <base-card>
    <header>
      <h3>{{ title }}</h3>
      <base-button mode="flat" type="button" @click="removeResource(id)">Delete</base-button>
    </header>
    <p>{{ description }}</p>
    <a :href="link" target="_blank">View Resource</a>
  </base-card>
</template>

<script>
export default {
  props: {
    id: {
      type: Number,
      required: true,
    },
    title: {
      type: String,
      required: true,
    },
    description: {
      type: String,
      required: true,
    },
    link: {
      type: String,
      required: true,
    },
  },
  inject: ['removeResource'],


};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
h3 {
  font-size: 1.25rem;
  margin: 0.5rem 0;
}
p {
  margin: 0.5rem 0;
}
a {
  text-decoration: none;
  color: #ce5c00;
}
a:hover,
a:active {
  color: #c89300;
}
</style>