<template>
  <div class="container">
    <div class="card">
      <div class="heading">
        <h4 class="title">Register to create a new account</h4>
      </div>
      <div class="content">
        <form @submit.prevent="handleSubmit">
          <div class="form-group">
            <label class="label" for="name">Name</label>
            <input
              v-model="name"
              type="text"
              class="form-control"
              id="name"
              placeholder="name"
              required
            />
          </div>
          <div class="form-group">
            <label class="label" for="email">Email address</label>
            <input
              v-model="email"
              type="email"
              class="form-control"
              id="email"
              placeholder="email"
              required
            />
          </div>
          <div class="form-group">
            <label class="label" for="password">Password</label>
            <input
              v-model="password"
              type="password"
              class="form-control"
              id="password"
              placeholder="password"
              required
            />
          </div>

          <button type="submit" class="btn">Submit</button>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "RegistrationForm",
  data: function() {
    return {
      name: "",
      email: "",
      password: ""
    };
  },
  methods: {
    async handleSubmit() {
      try {
        const response = await axios.post(
          "https://jsonplaceholder.typicode.com/posts",
          {
            name: this.name,
            email: this.email,
            password: this.password
          }
        );
        console.log("save info and redirect to profile");
      } catch (error) {
        console.log(error);
      }
    }
  }
};
</script>

<style scoped lang="scss">
.container {
  margin: 0 auto;
  max-width: 520px;
}
.title {
  font-size: 18px;
  font-weight: 600;
  margin-bottom: 18px;
}
.card {
  box-shadow: 0 2px 3px rgba(10, 10, 10, 0.1), 0 0 0 1px rgba(10, 10, 10, 0.1);
  padding: 24px;
}

.form-group {
  &:not(:last-child) {
    margin-bottom: 18px;
  }
}

.label {
  display: inline-block;
  margin-bottom: 0.5rem;
}

.form-control {
  display: block;
  width: 100%;
  padding: 0.375rem 0.75rem;
  font-size: 1rem;
  line-height: 1.5;
  color: #495057;
  background-color: #fff;
  background-clip: padding-box;
  border: 1px solid #ced4da;
  border-radius: 0.25rem;
}

.btn {
  color: #fff;
  cursor: pointer;
  background-color: #007bff;
  border-color: #007bff;
  padding: 8px 12px;
  border-radius: 6px;
  transition: all 0.1s ease-in;
  &:hover {
    background-color: #0069d9;
    border-color: #0062cc;
  }
}
</style>
