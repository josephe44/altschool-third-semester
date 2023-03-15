<template>
  <main>
    <div class="header_shadow"></div>
    <div class="user-container">
      <!-- user section -->
      <div class="user_section">
        <div class="user_profile_section">
          <div class="img-card">
            <img :src="user.avatar_url" alt="profile_img" />
          </div>
          <div class="user_profile_name">
            <h2>{{ user.name }}</h2>
            <p class="username">{{ user.login }}</p>
          </div>
        </div>
        <div class="group-btn">
          <div class="profile_btn">
            <button>View Profile</button>
          </div>
          <div class="repo_btn">
            <RouterLink to="/repos">
              <button>See Repos</button>
            </RouterLink>
          </div>
        </div>
      </div>
    </div>
    <!-- end of user section -->
    <!-- section for user information -->
    <section class="information_section">
      <div class="user_container_grid">
        <div class="user_container_bio">
          <!-- section for user information -->
          <h3>Personal information</h3>
          <div class="user_bio">
            <div class="email">
              <p>email {{ user.email ? user.email : 'eworlddata@gmail.com' }}</p>
            </div>
            <div class="location">
              <p>location {{ user.location }}</p>
            </div>
          </div>
        </div>
        <div class="user_container_bio">
          <!-- section for user information -->
          <h3>About Me</h3>
          <div class="user_bio">
            <p class="user-bio">{{ user.bio }}</p>
          </div>
        </div>
      </div>
      <div class="social_card_container">
        <h3>Statistics</h3>
        <div class="social_card">
          <p>followers</p>
          <span>{{ user.followers }}</span>
        </div>
        <div class="social_card">
          <p>public_repos</p>
          <span>{{ user.public_repos }}</span>
        </div>
        <div class="social_card">
          <p>following</p>
          <span>{{ user.following }}</span>
        </div>
        <div class="social_card">
          <p>public_gists</p>
          <span>{{ user.public_gists }}</span>
        </div>
      </div>
    </section>
  </main>
</template>

<script>
export default {
  name: 'HomeView',
  data() {
    return {
      user: {}
    }
  },
  async created() {
    const response = await fetch('https://api.github.com/users/josephe44')
    const data = await response.json()
    this.user = data

    console.log(data)
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
.user-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  max-width: 900px;
  width: 100%;
  position: relative;
  height: 200px;
}

.user_section {
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-wrap: wrap;
  position: absolute;
  top: -40px;
  left: 0;
  width: 100%;
  gap: 10px;
}

.user_profile_section {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 20px;
}

.user_profile_name h2 {
  font-size: 24px;
  line-height: 20px;
  font-weight: 700;
}
.user_profile_name p {
  font-size: 20px;
  line-height: 20px;
  font-weight: 500;
  margin-top: 10px;
}

.group-btn {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
}

.profile_btn button {
  background-color: #000000;
  width: 120px;
  color: #fff;
  padding: 10px 12px;
  border: none;
  /* border-radius: 5px; */
  cursor: pointer;
}
.repo_btn button {
  background-color: #fff;
  width: 120px;
  color: #000;
  padding: 10px 12px;
  border: 1px solid #000;
  /* border-radius: 5px; */
  cursor: pointer;
}

.information_section {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: flex-start;
  gap: 20px;
  width: 900px;
}

.user_container_grid {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.user_container_bio {
  background-color: #fff;
  padding: 20px 40px;
}

.user_container_bio h3 {
  font-size: 24px;
  line-height: 24px;
  font-weight: 600;
  color: #000;
}

.user_bio {
  display: flex;
  align-items: center;
  justify-content: flex-start;
  gap: 5px;
  margin-top: 20px;
}

.user_bio .email p,
.user_bio .location p {
  font-size: 16px;
  line-height: 24px;
  font-weight: 500;
}

.social_card_container {
  background-color: #fff;
  padding: 20px 20px;
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: flex-start;
}

.social_card_container h3 {
  font-size: 24px;
  line-height: 24px;
  font-weight: 600;
  color: #000;
  margin-bottom: 10px;
}

.social_card {
  gap: 50px;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 10px 0;
  border-bottom: 1px solid #d9d9d9;
}

.user {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  /* flex-wrap: wrap; */
  /* align-items: center; */
  gap: 10px;
  /* margin-bottom: 20px; */
}

.img-card {
  width: 200px;
  /* width: 100%; */
  height: 200px;
  border-radius: 50%;
  overflow: hidden;
  border: 11px solid #ffffff;
}

img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.user-details {
  display: flex;
  align-items: center;
  flex-direction: column;
  gap: 10px;
  /* margin-left: 20px; */
}
.user-details h2 {
  margin: 5px 0;
}

.user-details .username {
  font-size: 1.2rem;
  font-weight: 600;
  color: #002147;
}

.email,
.location {
  /* display: flex; */
  /* gap: 4px; */
  /* align-items: center; */
}
.contact {
  display: flex;
  align-items: center;
  flex-direction: column;
  /* gap: 8px; */
}

.user-bio {
  white-space: wrap;
  /* margin: 10px 0; */
  /* width: 300px; */
  /* font-size: 1rem; */
  /* color: #002147; */
}
.social-flex {
  /* display: flex;
  align-items: center;
  gap: 10px; */
}

/* @media (max-width: 950px) {
  .user_container_grid {
    flex: 0;
  }
} */

@media (max-width: 800px) {
  .user-container {
    height: 400px;
  }
  .user_section {
    left: 0;
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .user_profile_section {
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 5px;
  }

  .user_profile_name {
    text-align: center;
  }

  .information_section {
    width: 100%;
    flex-direction: column;
    align-items: center;
  }
  .user_container_grid {
    width: 100%;
  }
  .social_card_container {
    width: 100%;
  }
}

@media (max-width: 376px) {
  .group-btn {
    flex-direction: column;
    gap: 10px;
  }
}
</style>
