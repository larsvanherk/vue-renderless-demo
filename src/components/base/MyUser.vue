<template>
  <section class="my-user">
    <h1>My User</h1>

    <div class="my-user__input">
      <label for="firstname">First Name</label>
      <input
        type="text" id="firstname"
        v-model="user.firstName">
    </div>

    <div class="my-user__input">
      <label for="lastname">Last Name</label>
      <input
        type="text" id="lastname"
        v-model="user.lastName">
    </div>

    <button @click="insertBob()">Insert Bob</button>
  </section>
</template>

<script>
export default {
  data: () => ({
    user: {
      firstName: '',
      lastName: ''
    }
  }),

  watch: {
    user: {
      handler (val) {
        this.$emit('input:user', val);
      },
      deep: true
    }
  },

  methods: {
    insertBob () {
      this.user = {
        firstName: 'Bob',
        lastName: 'Marley'
      };
    }
  }
};
</script>

<style lang="scss">
.my-user {
  &__input {
    display: inline-block;
    width: 50%;

    &:not(:last-child) {
      width: 45%;
      margin-right: 5%;
    }

    label, input {
      display: block;
      width: 100%;

      box-sizing: border-box;
    }

    input {
      padding: 10px 20px;
    }
  }

  button {
    margin-top: 20px;
  }
}
</style>
