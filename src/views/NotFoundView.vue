<template>
  <div>
    <div class="container">
      <h1 className="erro_text">404</h1>
      <h2 className="not-found">
        <i class="fa-solid fa-face-sad-tear"></i>
        Oops, Page not Found!
      </h2>

      <RouterLink to="/" class="link">
        <p className="error-button"><i class="fa-solid fa-circle-left"></i> Go Back Home</p>
      </RouterLink>
    </div>
  </div>
</template>

<script>
export default {
  name: 'NotFoundView'
}
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  gap: 20px;
  align-items: center;
}
.erro_text {
  font-size: 100px;
  font-weight: 600;
  color: #000;
}
.link {
  text-decoration: none;
}
.error-button {
  text-align: center;
  background-color: #000000;
  width: 200px;
  color: #fff;
  padding: 10px 12px;
  border: none;
  cursor: pointer;
}
</style>
