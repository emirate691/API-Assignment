<template>
  <div class="home">
    <User />
  </div>
</template>

<script>
// @ is an alias to /src
import User from "../views/User.vue";
export default {
  name: "Home",
  components: {
    User
  }
};
</script>
