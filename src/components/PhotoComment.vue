<template>
  <div class="container">
    <div class="card">
      <div class="comment">
        <div class="comment__img">
          <img src="../assets/ts.jpg" alt="Profile picture" />
        </div>
        <div class="comment__content">
          <ul v-if="comments.length" class="comment-list">
            <li v-for="(item, index) in comments" :key="index">
              <span>{{item}}</span>
            </li>
          </ul>
          <div v-else class="no-comments">
            <p>No comments added yet</p>
          </div>
        </div>
        <div class="comment-box">
          <textarea
            @keyup.enter="addComment"
            v-model="newComment"
            class="form-control"
            rows="3"
            placeholder="Write a comment"
          ></textarea>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "PhotoComment",
  data: function() {
    return {
      newComment: "",
      comments: []
    };
  },
  methods: {
    addComment() {
      this.comments.push(this.newComment);
      this.newComment = "";
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
}

.comment {
  &__img {
    > img {
      width: 100%;
    }
  }
  &__content {
    padding: 18px;

    .comment-list {
      > li {
        &:not(:last-child) {
          margin-bottom: 12px;
        }
        > span {
          background-color: #f2f3f5;
          border-radius: 68px;
          padding: 8px 12px;
          font-size: 14px;
          display: inline-block;
        }
      }
    }
  }
  .comment-box {
    textarea {
      border: 1px solid #f2f2f2;
      width: 100%;
      padding: 12px;
    }
  }
}

.title {
  font-size: 18px;
  font-weight: 600;
  margin-bottom: 18px;
}
</style>
