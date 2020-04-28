<template>
  <div class="sidebar">
    <h2 class="sidebar__title"> Users</h2>
    <UserList :users="users" @userClick="$emit('userClick', $event)"/>
  </div>
</template>

<script>
import UserList from '@/components/UserList'

export default {
  components: {UserList},
  
  props: {
    users: Array
  }
}
</script>

<style lang="scss">
  .sidebar {
    padding-top: 1px;
    margin-top: -1px;

    &__title {
      padding: 0 10px;
      text-align: center;
    }
  }
</style>