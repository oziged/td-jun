<template>
  <div class="user-list">
    <div class="user-list__header">
      <div class="user-list__header-id">id</div>
      <div class="user-list__header-firstname">firstname</div>
      <div class="user-list__header-lastname">lastname</div>
    </div>

    <UserItem
      v-for="(user, index) in users" 
      :key="index"
      :user="user"
      @click.native="$emit('userClick', index)"
    />
  </div>
</template>

<script>
import UserItem from '@/components/UserItem'

export default {
  components: {UserItem},

  props: {
    users: Array
  }
}
</script>

<style lang="scss">
  .user-list {
    &__header {
      display: flex;
      padding: 10px;
      padding-top: 0;
      border-bottom: 2px solid rgba(0, 0, 0, 0.1);
      text-align: center;
    }

    &__header-id, &__header-firstname, &__header-lastname {
      width: calc(100% / 3);
    }
  }
</style>