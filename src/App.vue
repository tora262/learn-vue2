<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <AddNewUser 
      :title="title" 
      :isSuccessful="isSuccessful"
      @add-user="handleAdd" 
      @on-add="onAddUser" />
    <br><br>
    <UserList 
      :users="users"
      @on-delete="onDelete" />
  </div>
</template>

<script>
import AddNewUser from './components/AddNewUser.vue'
import UserList from './components/UserList.vue';

export default {
  name: 'App',
  components: {
    AddNewUser,
    UserList,
  },
  data: () => {
    return {
      title: "Adding Form:",
      user: {
        firstName: null,
        lastName: null,
      },
      users: [
        {
          id: 1,
          firstName: "Naruto",
          lastName: "Uzumaki"
        },
        {
          id: 2,
          firstName: "Sasuke",
          lastName: "Uchiha"
        },
        {
          id: 3,
          firstName: "Kakashi",
          lastName: "Hayate"
        }
      ],
      isSuccessful: false,
    }
  },
  methods: {
    handleAdd(user) {
      this.users.push({
        id: this.users.length + 1,
        firstName: user.firstName,
        lastName: user.lastName
      })
      this.isSuccessful = true
    },
    onAddUser() {
      this.isSuccessful = false
    },
    onDelete(deletedId) {
      this.users = this.users.filter(user => user.id !== deletedId)
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
