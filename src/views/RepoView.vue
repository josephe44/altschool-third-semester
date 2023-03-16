<template>
  <main>
    <div class="header_shadow"></div>
    <div class="go_back_btn">
      <RouterLink to="/repos">
        <button class="go_back">Go back</button>
      </RouterLink>
    </div>
    <div class="repo_container">
      <div class="repo_card">
        <div class="repo_items">
          <span>Repo Name:</span>
          <span> {{ repo.name }}</span>
        </div>
        <div class="repo_items">
          <span>Description:</span>
          <span>{{ repo.description ? repo.description : 'No Description yet' }}</span>
        </div>
        <div class="repo_items">
          <span>Language:</span>
          <span>{{ repo.language }}</span>
        </div>
      </div>
      <div class="repo_card">
        <div class="repo_items">
          <span>Created:</span>
          <span
            >{{ convertDate(repo.created_at) }}
            {{ getTime(repo.created_at) }}
          </span>
        </div>
        <div class="repo_items">
          <span>Updated:</span>
          <span>
            {{ convertDate(repo.updated_at) }}
            {{ getTime(repo.updated_at) }}
          </span>
        </div>
        <div class="repo_items">
          <span>Push:</span>
          <span>
            {{ convertDate(repo.pushed_at) }}
            {{ getTime(repo.pushed_at) }}
          </span>
        </div>
      </div>
      <div class="repo_card">
        <div class="repo_items">
          <span>Repo size:</span>
          <span>{{ repo.size }}kb</span>
        </div>
        <div class="repo_items">
          <span>Stars:</span>
          <span> {{ repo.stargazers_count }}</span>
        </div>
        <div class="repo_items">
          <span>Watchers:</span>
          <span> {{ repo.watchers_count }}</span>
        </div>
      </div>
      <div class="repo_card">
        <div class="repo_items">
          <span>Forks</span>
          <span>{{ repo.forks_count }}</span>
        </div>
        <div class="repo_items">
          <span>Issues:</span>
          <span>{{ repo.open_issues_count }}</span>
        </div>
        <div class="repo_items">
          <span>Subscribers:</span>
          <span>{{ repo.subscribers_count }}</span>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  name: 'RepoView',
  data() {
    return {
      repo: {}
    }
  },

  methods: {
    async fetchRepo() {
      const response = await fetch(
        `https://api.github.com/repos/josephe44/${this.$route.params.id}`
      )
      const data = await response.json()
      console.log(data)
      this.repo = data
    },

    convertDate(date) {
      const newDate = new Date(date)
      return newDate.toLocaleDateString()
    },
    // get time from date
    getTime(date) {
      const newDate = new Date(date)
      return newDate.toLocaleTimeString()
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

.go_back_btn {
  display: flex;
  align-items: flex-start;
  justify-content: flex-start;
  width: 100%;
}

.go_back_btn a {
  text-decoration: none;
}

.go_back {
  background-color: #fff;
  border: 1px solid #d9d9d9;
  border-radius: 5px;
  padding: 10px 10px;
  margin: 10px 0px;
  cursor: pointer;
}

.repo_container {
  background-color: #fff;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 20px;
  padding: 20px 20px;
  width: 100%;
}

.repo_items {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 10px 10px;
  justify-content: space-between;
  background-color: #d9d9d9;
}

.repo_items span:nth-child(1) {
  font-weight: bold;
  white-space: nowrap;
}

.repo_items span:nth-child(2) {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

@media (max-width: 768px) {
  .repo_container {
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  }
}
</style>
