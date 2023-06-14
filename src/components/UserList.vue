<template>
  <div>
    <div v-if="users.length <= 0">
      <div>The user list is empty. Please add one</div>
    </div>
    <div v-else>
      <table class="table">
        <thead>
          <tr>
            <th scope="col">#</th>
            <th scope="col">First</th>
            <th scope="col">Last</th>
            <th scope="col">Handle</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="user in users" :key="user.id">
            <th scope="row">{{ user.id }}</th>
            <td>{{ user.firstName }}</td>
            <td>{{ user.lastName }}</td>
            <td><button type="button" class="btn btn-danger" @click="onDelete(user.id)">Delete</button></td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>
<script>
export default {
  components: {
  },
  props: {
    users: Array
  },
  methods: {
    onDelete(deletedId) {
      this.$emit('on-delete', deletedId)
    } 
  }
};
</script>