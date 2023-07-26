<template>
  <footer>
    <p>Copyright &copy; 15/7/2023</p>
    <div v-show="homePage">
      <router-link to="/about" >About</router-link>
      
    </div>
  </footer>
</template>
<script>
export default{
  computed: {
    homePage() {
      if (this.$route.path === '/') {
        return true
      } else {
        return false
      }
    },
  }
}
</script>

<style scoped>
a {
  color: #333;
}

footer {
  margin-top: 30px;
  text-align: center;
}
</style>
