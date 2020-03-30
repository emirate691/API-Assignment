<template>
  <div>
    <b-container class="bv-example-row" fluid:width="100%">
      <b-row>
        <b-col class="text-left  mx-auto" lg="6">
          <div class="container" id="header">
            <h3 class="head">List of user</h3>
            <input type="text" id="put" v-model="name" />
            <button @click="addUser" class="btn">Add</button>
          </div>
          <b-list-group>
            <b-list-group-item
              button
              class="d-flex justify-content-between align-items-center"
              v-for="user in users"
              :key="user.id"
              >{{ user.name
              }}<span class="close" @click="removeUser(user)">x</span>
            </b-list-group-item>
          </b-list-group>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>
<script>
import axios from "axios";

export default {
  data() {
    return {
      users: [],
      name: null
    };
  },
  methods: {
    addUser() {
      this.users.push({ name: this.name });
      this.name = null;
    },
    removeUser(user) {
      this.users.splice(this.users.indexOf(user), 1);
    }
  },

  async created() {
    let fetchUsers = await axios.get(
      "https://jsonplaceholder.typicode.com/users"
    );
    console.log("my item", fetchUsers);
    this.users = fetchUsers.data;
  }
};
</script>
<style>
body {
  margin: 0;
  min-width: 250px;
}
.container {
  max-width: 1200px;
  margin: 0 auto;
}
#put {
  width: 80%;
  height: 44px;
}
.btn {
  width: 20%;
}
* {
  border-box: box-sizing;
}
#header {
  background-color: #c66438;
  padding: 30px 40px;
  color: white;
  text-align: center;
}
.head {
  text-align: centre;
}
</style>
