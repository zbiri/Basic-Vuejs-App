<template>
    <div class="users">
      <div class="fluid-container">
      <h1>Users</h1>
      <form v-on:submit="addUser">


           <input type="text" v-model="newUser.name" id="form3" class="form-control" placeholder="User Name">
        <br>
       <input type="text" v-model="newUser.email" placeholder="User Email" class="form-control">
        <br>
        <input type="submit" value="Submit" class="btn btn-secondary">
      </form>
      <ul>
        <li v-for="user in users">

              <input type="checkbox" id="checkbox1" v-model="user.contacted">
          <span :class="{contacted: user.contacted}">
            {{user.name}}: {{user.email}}
          </span>&nbsp;&nbsp;
          <button type="button" class="btn btn-danger btn-sm" v-on:click="deleteUser(user)">&times</button>
        </li>
      </ul>
      <br><br>
       </div>
    </div>
</template>

<script>
    export default {
        name: 'users',

        data() {
            return {
                newUser: {},
                users: []
            }
        },
      methods: {
          addUser: function(e){
            this.users.push({
              name: this.newUser.name,
              email: this.newUser.email,
              contacted: false
            });
            this.newUser = {};
            e.preventDefault();
          },
          deleteUser: function(user) {
            this.users.splice(this.users.indexOf(user), 1);
          }

      },
      created: function() {
        this.$http.get('https://jsonplaceholder.typicode.com/users').then(response =>{
          console.log(response.data);
             this.users = response.data;
            })
      }

    }
</script>

<style scoped>
  .contacted{
    text-decoration: line-through;
  }
  li{
    text-decoration: none;
  }
</style>
