<template>
  <main>
    <div class="header_shadow"></div>
    <!-- ui card for git repo card list grid view -->
    <div class="repo_container_grid">
      <ul v-for="repo in paginateRepo" :key="repo.id">
        <li>{{ repo.name }}</li>
        <div class="repo_btn">
          <RouterLink :to="{ name: 'repo', params: { id: repo.id } }">
            <button>View</button>
          </RouterLink>
        </div>
      </ul>
    </div>
    <div class="pagination_container">
      <button
        @click="currentPage--"
        :disabled="currentPage === 1"
        :class="{ disabled: currentPage === 1 }"
      >
        Prev
      </button>
      <span>Page {{ currentPage }} of {{ totalPage }}</span>
      <button
        @click="currentPage++"
        :disabled="currentPage === totalPage"
        :class="{ disabled: currentPage === totalPage }"
      >
        Next
      </button>
    </div>
  </main>
</template>

<script>
export default {
  name: 'ReposView',
  data() {
    return {
      repos: [],
      currentPage: 1,
      perPage: 12,
      totalPage: 0
    }
  },

  methods: {
    async fetchRepo() {
      const response = await fetch('https://api.github.com/users/josephe44/repos')
      const data = await response.json()
      this.totalPage = Math.ceil(data.length / this.perPage)
      this.repos = data
    }
  },

  computed: {
    paginateRepo() {
      const startIndex = (this.currentPage - 1) * this.perPage
      const endIndex = startIndex + this.perPage
      return this.repos.slice(startIndex, endIndex)
    }
  },

  mounted() {
    this.fetchRepo()
  }
}
</script>

<style scoped>
main {
  /* min-height: 100vh; */
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding-bottom: 40px;
}

.header_shadow {
  height: 165px;
  width: 100%;
  background-color: #d9d9d9;
}

.repo_container_grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  grid-gap: 10px;
  width: 100%;
  /* max-width: 900px; */
  padding: 10px 0;
  width: 100%;
}

ul {
  list-style: none;
  background-color: #fff;
  border-radius: 5px;
  padding: 10px 20px;
  display: flex;
  gap: 20px;
  flex-direction: column;
  /* align-items: flex-end; */
  /* justify-content: flex-end; */
  width: 100%;
}

li {
  text-align: left;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  text-transform: capitalize;
}

.repo_btn {
  display: flex;
  align-items: center;
  justify-content: flex-end;
  width: 100%;
}

button {
  background-color: #fff;
  width: 60px;
  color: #000;
  padding: 8px 12px;
  border: 1px solid #e8e8e8;
  /* border-radius: 5px; */
  cursor: pointer;
}

.pagination_container {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  margin-top: 40px;
}

.disabled {
  cursor: not-allowed;
  opacity: 0.5;
}
</style>
