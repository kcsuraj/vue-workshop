<template>
  <div>
    <ul class="list">
      <li v-for="(news, index) in stories" :key="index">
        <template v-if="news.title">
          <a :href="news.url">{{news.title}}</a>
          <span>By: {{news.author}}</span>
        </template>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Stories",
  props: ["stories"]
};
</script>

<style scoped lang="scss">
.list {
  > li {
    &:not(:last-child) {
      margin-bottom: 18px;
    }
    > a {
      color: #0a5b8c;
      display: block;
      margin-bottom: 6px;
    }

    > span {
      color: rgba(#3b4242, 0.7);
      font-size: 12px;
    }
  }
}
</style>