<template>
  <div class="friend-card">
    <h1 :style="{color: friend.isFavourite ? 'red' : 'black'}" @click="addToFavourites">{{ friend.name }} <span @click="toggleShowMore">Details</span></h1>
    <div class="show-more" v-if="showMore">
      <p>ID: {{ friend.id }}</p>
      <p>Phone: {{ friend.phone }}</p>
      <p>E-mail: <a :href="'mailto:' + friend.email">{{ friend.email }}</a></p>
    </div>
  </div>
</template>

<script>
export default {
  name: "FriendCard",
  props: {
    friend: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      showMore: false
    }
  },
  methods: {
    toggleShowMore() {
      this.showMore = !this.showMore
    },
    addToFavourites() {
      this.$emit('add-to-favourites', this.friend.id)
    }
  }
}
</script>

<style scoped>
.friend-card {
  border: 1px solid crimson;
  width: 400px;
  border-radius: 10px;
  margin-bottom: 10px;
}

.friend-card span {
  font-size: 11px;
  border-left: 3px solid crimson;
  padding: 2px 5px;
  transition: background-color 1s, color 1s;
}

.friend-card span:hover {
  cursor: pointer;
  background-color: crimson;
  color: white;
  transition: background-color 1s, color 1s;
}

.show-more {
  padding: 0 20px;
  text-align: left;
}
</style>
