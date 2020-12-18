<template>
  <div class="friend-card">
    <h1><span :style="{color: friend.isFavourite ? 'orange' : 'black'}" @click="addToFavourites">☆</span> {{ friend.name }}</h1>
    <span class="details" @click="toggleShowMore">Show details</span>
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
  emits: ['add-to-favourites'],
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

.friend-card .details {
  font-size: 11px;
  border-bottom: 3px solid crimson;
  padding: 2px 5px;
  transition: background-color 1s, color 1s;
}

.friend-card .details:hover {
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
