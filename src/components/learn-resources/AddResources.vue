<template>
  <base-dialog
    v-if="inputIsInvalid"
    title="Invalid Input"
    @close="confirmError"
  >
    <template #default>
      <p style="margin-bottom: 1rem">
        Unfortunately, atleast one input value is invalid
      </p>
      <p>
        Please check all inputs and make sure you enter at least a few
        characters into each input field
      </p>
    </template>
    <template #actions>
      <base-button @click="confirmError">Okay</base-button>
    </template>
  </base-dialog>
  <base-card>
    <form @submit.prevent="submitResource">
      <div class="form-group">
        <label for="title">Title</label>
        <input
          type="text"
          name="title"
          id="title"
          v-model="newResource.title"
        />
      </div>
      <div class="form-group">
        <label for="description">Description</label>
        <textarea
          name="description"
          id="description"
          rows="3"
          v-model="newResource.description"
        ></textarea>
      </div>
      <div class="form-group">
        <label for="link">Link</label>
        <input type="url" name="link" id="link" v-model="newResource.link" />
      </div>
      <div>
        <base-button type="submit">submit</base-button>
      </div>
    </form>
  </base-card>
</template>
<script>
export default {
  inject: ["addNewResource"],
  data() {
    return {
      inputIsInvalid: false,
      newResource: {
        id: 0,
        title: "",
        description: "",
        link: "",
      },
    };
  },
  methods: {
    submitResource() {
      console.log(this.newResource);
      if (
        this.newResource.title.trim() == "" ||
        this.newResource.description.trim() == "" ||
        this.newResource.link.trim() == ""
      ) {
        return (this.inputIsInvalid = true);
      }
      this.addNewResource(this.newResource);
      this.newResource = {
        id: 0,
        ttle: "",
        description: "",
        link: "",
      };
    },
    confirmError() {
      this.inputIsInvalid = false;
    },
  },
};
</script>
<style scoped>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}
input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}
input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}
.form-group {
  margin: 1rem 0;
}
</style>