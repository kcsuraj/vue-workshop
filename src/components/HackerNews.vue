<template>
  <div class="container">
    <div class="card">
      <div class="heading">
        <h4 class="title">Netflix Ratings</h4>
      </div>
      <search @title="handleTitleChange"></search>
      <div class="content">
        <div v-if="loading">
          <p>Loading news</p>
        </div>
        <stories :stories="stories"></stories>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Search from "./Search";
import Stories from "./Stories";
export default {
  name: "HackerNews",
  data() {
    return {
      loading: true,
      stories: []
    };
  },
  components: {
    Search,
    Stories
  },
  created: async function() {
    this.getData();
  },
  methods: {
    async handleTitleChange(title) {
      this.getData(title);
    },
    async getData(title = "") {
      try {
        const response = await axios.get(
          "http://hn.algolia.com/api/v1/search",
          {
            params: {
              query: title
            }
          }
        );
        this.stories = response.data.hits;
      } catch (error) {
        console.log(error);
      } finally {
        this.loading = false;
      }
    }
  }
};
</script>

<style scoped lang="scss">
.container {
  margin: 0 auto;
  max-width: 768px;
}

.card {
  box-shadow: 0 2px 3px rgba(10, 10, 10, 0.1), 0 0 0 1px rgba(10, 10, 10, 0.1);
  padding: 24px;
}

.btn {
  color: #fff;
  cursor: pointer;
  background-color: #117a8b;
  border-color: #10707f;
  border: 1px solid transparent;
  padding: 6px 12px;
  border-radius: 6px;
  transition: all 0.1s ease-in;
  &:hover {
    background-color: #138496;
    border-color: #117a8b;
  }
}

.heading {
  margin-bottom: 12px;

  .title {
    font-size: 18px;
    font-weight: 600;
  }
}
</style>