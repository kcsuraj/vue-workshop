
<template>
  <div id="app">
    <form-component :fields="fields" @success="successCallback" :endpoint="endpoint">
      <template slot="form-header">
        <div class="heading">
          <h4 class="title">Register to create a new account</h4>
        </div>
      </template>
      <template slot="form-fields" slot-scope="slotProps">
        <div class="form-group">
          <label class="label" for="title">Title</label>
          <input
            v-model="fields.title"
            type="text"
            class="form-control"
            id="title"
            placeholder="Title"
          />
          <p>{{slotProps.error}}</p>
        </div>
        <div class="form-group">
          <label class="label" for="desc">Description</label>
          <input
            v-model="fields.body"
            type="text"
            class="form-control"
            id="desc"
            placeholder="Description"
          />
        </div>
        <div class="form-group">
          <label class="label" for="id">ID</label>
          <input
            v-model="fields.userId"
            type="number"
            class="form-control"
            id="id"
            placeholder="ID"
          />
        </div>

        <div class="alert alert-danger" role="alert" v-if="slotProps.error">{{slotProps.error}}</div>
      </template>

      <template slot="submit">
        <button type="submit" class="btn">Submit</button>
      </template>
    </form-component>
  </div>
</template>

<script>
import FormComponent from "./components/FormComponent.vue";

export default {
  name: "app",
  components: {
    FormComponent
  },
  data: function() {
    return {
      endpoint: "https://jsonplaceholder.typicode.com/posts",
      fields: {
        title: "",
        body: "",
        userId: 0
      }
    };
  },
  methods: {
    successCallback(data) {
      console.log(data);
    },
    errorCallback(error) {
      console.log("error", error.message);
    }
  }
};
</script>

<style lang="scss">
@import "./styles/main.scss";

#app {
  margin-top: 60px;
}
</style>
