<template>
  <div class="user-item">
    <div class="user-item__id" :title="user.login.uuid">{{ slice(user.login.uuid, 5) }}</div> <!-- использовал uuid, а не id, т.к. id не всегда приходил -->
    <div class="user-item__firstname">{{ user.name.first }}</div>
    <div class="user-item__lastname">{{ user.name.last }}</div>
  </div>
</template>

<script>
export default {
  props: {
    user: Object
  },

  methods: {
    slice(str, limit) {
      if (str.length <= limit) return
      else return str.slice(0, 5) + '...'
    }
  }
}
</script>

<style lang="scss">
  .user-item {
    display: flex;
    padding: 10px;
    cursor: pointer;

    &:hover {
      background: #f6f6f6;
    }

    &__id, &__firstname, &__lastname {
      width: calc(100% / 3);
      text-align: center;
    }
  }
</style>