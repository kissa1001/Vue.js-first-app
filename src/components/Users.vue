<template>
  <div class="users">
    <h1>Users</h1>
    <form v-on:submit="addUser">
      <input type="text" v-model="newUser.name" placeholder="Enter Name">
      <br>
      <input type="text" v-model="newUser.email" placeholder="Enter Email">
      <br>
      <button type="submit" value="Submit">Submit</button>
    </form>
    <ul>
      <li v-for="user in users">
        <input type="checkbox" class="toggle" v-model="user.contacted">
        <span :class="{contacted: user.contacted}">
          {{user.name}}: {{user.email}}
          <button type="button" v-on:click="deleteUser(user)">X</button>
        </span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'users',
  data () {
    return {
      newUser: {},
      users: [
        {
          name: 'John Doe',
          email: 'jdoe@mail.com',
          contacted: false
        },
        {
          name: 'Steve Smith',
          email: 'ssmith@mail.com',
          contacted: false
        },
        {
          name: 'Tom White',
          email: 'twhite@mail.com',
          contacted: false
        }
      ]
    }
  },
  methods: {
    addUser: function (e) {
      e.preventDefault()
      this.users.push({
        name: this.newUser.name,
        email: this.newUser.email,
        contacted: false
      })
    },
    deleteUser: function (user) {
      this.users.splice(this.users.indexOf(user), 1)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h1, h2 {
    font-weight: normal;
  }
  .contacted {
    text-decoration: line-through;
  }
</style>
