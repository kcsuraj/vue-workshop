<template>
  <div class="container">
    <div class="card">
      <div class="filters">
        <div>
          <h4 class="title">Netflix Ratings</h4>
          <div class="actions">
            <button @click="sortLowest" class="btn">Lowest rated</button>
            <button @click="sortHighest" class="btn">Highest rated</button>
          </div>
        </div>
        <div class="search">
          <input v-model="title" type="text" class="form-control" placeholder="Search by title" />
        </div>
      </div>
      <div class="content">
        <table class="table">
          <thead>
            <th v-for="(key, index) in columns" :key="index">{{key}}</th>
          </thead>
          <tbody>
            <tr v-for="(entry, index) in filteredMovies" :key="index">
              <td v-for="(key, index) in columns" :key="index">{{entry[key]}}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "NetflixRatings",
  data: function() {
    return {
      title: "",
      columns: ["title", "rating"],
      ratingsInfo: [
        { title: `Grey's Anatomy`, rating: 98 },
        { title: `Prison Break`, rating: 98 },
        { title: `How I Met Your Mother`, rating: 94 },
        { title: `Supernatural`, rating: 95 },
        { title: `Breaking Bad`, rating: 97 },
        { title: `The Vampire Diaries`, rating: 91 },
        { title: `The Walking Dead`, rating: 98 },
        { title: `Pretty Little Liars`, rating: 96 },
        { title: `Once Upon a Time`, rating: 98 },
        { title: `Sherlock`, rating: 95 },
        { title: `Death Note`, rating: 77 },
        { title: `Naruto`, rating: 88 },
        { title: `Arrow`, rating: 96 },
        { title: `Black Mirror`, rating: 80 },
        { title: `The Originals`, rating: 74 },
        { title: `The 100`, rating: 97 },
        { title: `Masha and the Bear`, rating: 81 },
        { title: `Hunter X Hunter`, rating: 57 },
        { title: `Marvel's Luke Cage`, rating: 95 },
        { title: `Marvel's Iron Fist`, rating: 98 }
      ]
    };
  },
  computed: {
    filteredMovies() {
      return this.ratingsInfo.filter(info => {
        return info.title.toLowerCase().match(this.title.toLowerCase());
      });
    }
  },
  methods: {
    sortLowest() {
      this.ratingsInfo.sort((a, b) => (a.rating > b.rating ? 1 : -1));
    },
    sortHighest() {
      this.ratingsInfo.sort((a, b) => (a.rating < b.rating ? 1 : -1));
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

.table {
  width: 100%;
  margin-bottom: 24px;
  thead {
    th {
      border-bottom: 2px solid #ccc;
      text-align: left;
      font-weight: 600;
    }
  }
  td,
  th {
    padding: 0.75rem;
    vertical-align: top;
    border-top: 1px solid #dee2e6;
  }
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

.filters {
  > div {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 12px;
  }

  margin-bottom: 18px;

  .title {
    font-size: 18px;
    font-weight: 600;
  }

  .btn {
    &:first-child {
      margin-right: 12px;
    }
  }

  .search {
    .form-control {
      background-color: transparent;
      border: none;
      border-bottom: 1px solid #ced4da;
      border-radius: 0;
      outline: 0;
      box-shadow: none;
      padding: 6px 0;
      width: 100%;
    }
  }
}
</style>
