<template>
  <h1>VUE Friends List</h1>
  <div class="buttons">
    <button @click="showAddNewFriendForm = !showAddNewFriendForm">+</button>
  </div>
  <new-friend v-if="showAddNewFriendForm" @add-new-friend="addNewFriend"/>
  <div class="friends-container">
    <friend-card
        v-for="friend in friends"
        :key="friend.id"
        :friend="friend"
        @add-to-favourites="addToFavourites"
        @delete-friend="deleteFriend"
    />
    <p v-if="friends.length <= 0">No friends in the list</p>
  </div>
</template>

<script>
import FriendCard from "@/components/FriendCard";
import NewFriend from "@/components/NewFriend";

export default {
  name: 'App',
  components: {
    FriendCard, NewFriend
  },
  data() {
    return {
      showAddNewFriendForm: false,
      friends: [
        {
          id: 'petras77',
          name: 'Petras Petrauskelis',
          phone: '370 601 44030',
          email: 'petras@petrauskelis.lt',
          isFavourite: false
        },
        {
          id: 'onute66',
          name: 'Ona Bubrauskaite',
          phone: '370 647 00556',
          email: 'ona@index.lt',
          isFavourite: false
        },
        {
          id: 'onute21',
          name: 'Ona Bubrauskaite',
          phone: '370 647 00556',
          email: 'ona@index.lt',
          isFavourite: false
        },
        {
          id: 'onute29',
          name: 'Ona Bubrauskaite',
          phone: '370 647 00556',
          email: 'ona@index.lt',
          isFavourite: false
        },
        {
          id: 'onute23',
          name: 'Ona Bubrauskaite',
          phone: '370 647 00556',
          email: 'ona@index.lt',
          isFavourite: true
        },
        {
          id: 'onute22',
          name: 'Ona Bubrauskaite',
          phone: '370 647 00556',
          email: 'ona@index.lt',
          isFavourite: false
        },
      ],
    }
  },
  methods: {
    addToFavourites(friendId) {
      const user = this.friends.find(x => x.id === friendId)
      user.isFavourite = !user.isFavourite
    },
    addNewFriend(friendObj) {
      this.friends.push(friendObj)
      this.showAddNewFriendForm = false
    },
    deleteFriend(friendId) {
      this.friends = this.friends.filter(x => x.id !== friendId)
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

.friends-container {
  display: flex;
  justify-content: space-evenly;
  flex-wrap: wrap;
}

.buttons {
  margin-bottom: 10px;
}

button {
  margin-top: 10px;
  padding: 5px 15px;
  background-color: crimson;
  border: none;
  color: white;
  text-transform: uppercase;
  outline: none;
  cursor: pointer;
}

span {
  cursor: pointer;
}
</style>
