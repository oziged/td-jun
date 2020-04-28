<template>
  <div class="app-container">
    <Sidebar class="app-sidebar" :users="users" @userClick="setActiveUser"/>
    <UserFullBlock 
      :user="activeUser"
    />
  </div>
</template>

<script>
import Sidebar from '@/components/Sidebar'
import UserFullBlock from '@/components/UserFullBlock'
import axios from 'axios'

export default {
  components: {Sidebar, UserFullBlock},
  
  data() {
    return {
      users: [],
      activeUser: null,
      isLoading: true      
    }
  },


  created() {
    this.fetchUsers()
  },  


  methods: {
    setActiveUser(id) {
      this.activeUser = this.users[id]
    },

    fetchUsers() {
      axios.get('https://randomuser.me/api/?results=20')
        .then(({data: {results: users}}) => {
          this.users = users
          this.isLoading = false
        })
    }
  },
}
</script>

<style lang="scss">
  html body {
    background: rgb(250, 250, 250);
    font-family: 'Manrope', sans-serif;
  }

  .app-sidebar {
    width: 400px;
    min-height: 100vh;
    border-right: 2px solid rgba(0, 0, 0, .1);
  }

  .app-container {
    display: flex;
  }
</style>
