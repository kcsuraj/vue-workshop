<template>
  <div class="container">
    <div class="card">
      <slot name="form-header"></slot>
      <div class="content">
        <form @submit.prevent="save">
          <slot name="form-fields" :error="error"></slot>
          <slot name="submit"></slot>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "FormComponent",

  props: ["fields", "endpoint"],
  data: function() {
    return {
      error: null
    };
  },
  methods: {
    async save() {
      try {
        const response = await axios.post(this.endpoint, this.fields);
        this.$emit("success", response.data);
      } catch (error) {
        this.error = error.message;
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
  margin-bottom: 18px;
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

.alert {
  padding: 12px;
  border-radius: 6px;
  margin-bottom: 12px;
  color: #721c24;
  background-color: #f8d7da;
  border-color: #f5c6cb;
}
</style>
