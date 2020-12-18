<template>
  <h1>VUE Friends List</h1>
  <div class="friends-container" >
  <FriendCard v-for="friend in friends" :key="friend.id" :friend="friend" @add-to-favourites="addToFavourites"/>
  </div>
</template>

<script>
import FriendCard from "@/components/FriendCard";

export default {
  name: 'App',
  components: {
    FriendCard
  },
  data() {
    return {
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
</style>
