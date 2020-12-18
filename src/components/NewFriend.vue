<template>
  <div class="new-friend-form">
    <form @submit.prevent="submitData">
      <div>
        <label>Name</label>
        <input type="text" v-model="newFriend.name"/>
      </div>
      <div>
        <label>Phone</label>
        <input type="tel" v-model="newFriend.phone"/>
      </div>
      <div>
        <label>Email</label>
        <input type="email" v-model="newFriend.email"/>
      </div>
      <div>
        <button>Add new friend</button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  emits: ['add-new-friend'],
  data() {
    return {
      newFriend: {
        id: '',
        name: '',
        phone: '',
        email: ''
      }
    }
  },
  methods: {
    submitData() {
      this.newFriend.id = new Date().toISOString()
      this.$emit('add-new-friend', this.newFriend)
    }
  }
}
</script>

<style scoped>
.new-friend-form {
  width: 400px;
  margin: 0 auto 10px auto;
  padding: 15px;
  border-radius: 10px;
  box-sizing: border-box;
}

label {
  display: inline-block;
  width: 20%;
  text-align: right;
  padding-right: 10px;
  box-sizing: border-box;
}

input {
  width: 40%;
  border: 1px solid black;
  border-radius: 5px;
  padding: 5px;
  box-sizing: border-box;
  outline: none;
  margin-bottom: 5px;
}

</style>
