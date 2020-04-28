<template>
  <div class="user-full-block">
    <div 
      class="user-full-block__list"
      v-if="user"
    >
      <div 
        class="user-full-block__row"
        v-for="(value, key, index) in formattedInfo" :key="index"
      >
        <div class="user-full-block__row-key">
          {{ key }} ->
        </div>
        <div class="user-full-block__row-value">
          {{ value }}
        </div>
      </div>
    </div>
    <div
      v-else
    >
      Select some user please 🙃
    </div>
  </div>
</template>

<script>
export default {
  props: {
    user: Object
  },


  computed: {
    formattedInfo() {
      if (!this.user) return

      return {
        location: `${this.user.location.city}, ${this.user.location.country}`,
        email: this.user.email,
        gender: this.user.gender,
        birthday: new Date(this.user.dob.date).toDateString(),
        'phone-number': this.phone
      }
    }
  }
}
</script>

<style lang="scss">
  .user-full-block {
    width: calc(100% - 400px);
    font-size: 2rem;
    line-height: 150%;
    padding: 25px;

    &__row {
      width: 100;
      display: flex;
    }
  }
</style>