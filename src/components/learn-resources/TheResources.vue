<template>
  <base-card>
    <base-button
      @click="setSelectedTab('stored-resources')"
      :mode="storedResetButtonMode"
      type="button"
      >Stored Resources</base-button
    >
    <base-button
      @click="setSelectedTab('add-resources')"
      :mode="AddResetButtonMode"
      type="button"
      >Add Resources</base-button
    >
  </base-card>
  <keep-alive>
    <component :is="selectedTab"></component>
  </keep-alive>
</template>

<script>
import AddResources from "./AddResources.vue";
import StoredResources from "./StoredResources.vue";
export default {
  components: {
    AddResources,
    StoredResources,
  },
  data() {
    return {
      selectedTab: "stored-resources",
      storedResources: [
        {
          id: 1,
          title: "Official Documentation",
          description: "The official VueJs documentation.",
          link: "https://vuejs.org",
        },
        {
          id: 2,
          title: "Google",
          description: "Learn how to google...",
          link: "https://google.org",
        },
      ],
    };
  },
  computed: {
    storedResetButtonMode() {
      return this.selectedTab === "stored-resources" ? null : "flat";
    },
    AddResetButtonMode() {
      return this.selectedTab === "add-resources" ? null : "flat";
    },
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
    addNewResource(newResource) {
      newResource.id = this.storedResources.length + 1;
      this.storedResources.unshift(newResource);
      this.selectedTab = "stored-resources";
    },
    deleteResource(resourceId) {
      const resIndex = this.storedResources.findIndex(
        (resource) => resource.id == resourceId
      );
      this.storedResources.splice(resIndex, 1);
    },
  },
  provide() {
    return {
      resources: this.storedResources,
      addNewResource: this.addNewResource,
      removeResource: this.deleteResource,
    };
  },
};
</script>