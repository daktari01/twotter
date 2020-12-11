<template>
  <UserProfile/>
</template>

<script>
import UserProfile from './components/UserProfile'

export default {
  name: 'App',
  components: {
    UserProfile
  },
  data() {
    return {
      followers: 0,
      user: {
        id: 1,
        username: 'daktari',
        firstName: 'James',
        lastName: 'Daktari',
        email: 'daktari@gmail.com',
        isAdmin: true
      }
    }
  },
  watch: {
    followers(newFollowerCount, oldFollowerCount) {
      if (oldFollowerCount < newFollowerCount) {
        console.log(`${this.user.username} has gained a follower!`);
      }
    }
  },
  computed: {
    fullName() {
      return `${this.user.firstName} ${this.user.lastName}`;
    }
  },
  methods: {
    followUser() {
      this.followers++
    }
  },
  mounted() {
    this.followUser();
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  min-height: 100vh;
  background-color: #F3F5FA;
}
</style>
