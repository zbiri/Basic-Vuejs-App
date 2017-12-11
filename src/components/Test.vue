<template>
    <div class="test">
      <h1>{{title}}</h1>
      <p v-if="showName" >{{user.first_name}}</p>
      <p v-else>{{user.last_name}}</p>
      <ul>
        <li v-for="item in items">{{item.title}}</li>
      </ul>

      <input type="text" v-model="title"><br><br>
      <button v-on:click="greet">Reset</button>
      <br><br>
      <h3>{{fullName}}</h3><br>
      {{msg}}

    </div>
</template>

<script>
    export default {
        name: 'test',
        props: {
          msg: {
            type: String,
            default: 'Foobar'
          }
        },
        data() {
            return {
                title: '',
              user: {
                  first_name : 'said',
                  last_name : 'zbiri'
              },
              showName: false,
              items : [
                {title: 'One'},
                {title: 'two'},
                {title: 'tree'},

              ]



            }
        },
      methods: {
          greet: function(){
            this.title = 'hallo world';

          }
      },
      computed: {
          fullName: function(){
            return this.user.first_name + ' '+this.user.last_name;
          }
      }



    }
</script>

<style scoped>

</style>
