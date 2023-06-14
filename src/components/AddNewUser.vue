<template>
    <div>
        <h2>{{title}}</h2>
        <div class="input-group flex-nowrap">
            <span class="input-group-text" id="addon-wrapping">@</span>
            <input v-model="user.firstName"
                    @input="onAddNew"
                    type="text" class="form-control" placeholder="FirstName" aria-label="FirstName"
                    aria-describedby="addon-wrapping">
        </div>
        <div class="input-group flex-nowrap">
            <span class="input-group-text" id="addon-wrapping">@</span>
            <input v-model="user.lastName"
                    @input="onAddNew"
                    type="text" class="form-control" placeholder="LastName" aria-label="LastName"
                    aria-describedby="addon-wrapping">
        </div>
        <div class="messageError" v-if="messageError">{{messageError}}</div>
        <div class="messageSuccess" v-if="isSuccessful">Add Successfully</div>

        <br />

        <div>
            <button type="button" class="btn btn-success" @click="handleAdd">Add</button>
        </div>
    </div>
</template>
<script>
export default {
  components: {
  },
  props: {
    title: String,
    isSuccessful: Boolean
  },
  data: () => {
    return {
      user: {
        firstName: null,
        lastName: null,
      },
      messageError: null,
    }
  },
  methods: {
    handleAdd() {
      if(!this.user.firstName || !this.user.lastName) {
        this.messageError = 'Input cannot be empty'
      } else {
        this.$emit('add-user', this.user)
        this.user.firstName = null
        this.user.lastName = null
      }
    },
    onAddNew() {
      this.$emit('on-add')
      this.messageError = null
    }
  }
};
</script>