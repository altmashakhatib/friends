<template>
  <AddFriends></AddFriends>
  <button @click="getFriends">Get Friends</button>
  <br>
  <p v-if="loading">Loading..</p>

  <FriendsDetails
    v-for="detail in details"
    :key="detail.name"
    :data="detail"
  ></FriendsDetails>
</template>

<script>
import AddFriends from "./components/AddFriends.vue";
import FriendsDetails from "./components/FriendsDetails.vue";

export default {
  components: {
    AddFriends,
    FriendsDetails,
  },
  data() {
    return {
      details: [],
      loading:false
    };
  },
  methods: {
    async getFriends() {
      this.loading=true
      const response = await fetch(
        "https://friends-eebcf-default-rtdb.firebaseio.com/friends.json"
      );
      if(response.ok){
        this.details = await response.json();
      this.loading=false
      }
      else{
        alert("Error")
        this.loading=false
      }
     



    },
  },
};
</script>
<style scoped>
  body {
    font-family: Arial, sans-serif;
    padding: 20px;
  }

  button {
    padding: 10px 20px;
    background-color: #3498db;
    color: #fff;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    margin-bottom: 20px;
  }

  button:hover {
    background-color: #2980b9;
  }

  p {
    margin-top: 10px;
    display: inline-block;
    font-weight: bold;
  }
</style>

