<template>
  <section class="my-user">
    <my-user-rl @input:user="$emit('input:user', $event)">
      <template
        v-slot:default="{
          user,
          updateUser,
          insertBob
        }">
        <section>
          <h1>My User</h1>

          <div class="my-user__input">
            <label for="firstname">First Name</label>
            <input type="text" id="firstname"
              :value="user.firstName"
              @input="updateUser({ firstName: $event.target.value })" />
          </div>

          <div class="my-user__input">
            <label for="lastname">Last Name</label>
            <input type="text" id="lastname"
              :value="user.lastName"
              @input="updateUser({ lastName: $event.target.value })" />
          </div>

          <button @click="insertBob()">Insert Bob</button>
        </section>
      </template>
    </my-user-rl>
  </section>
</template>

<script>
import MyUserRl from './MyUser.rl';

export default {
  components: {
    MyUserRl
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
