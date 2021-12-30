<template>
  <b-container id="app">
      <UsersCard
         class="user"
         v-for="user in users"
         :key="user.first"
         :imgSrc="user.picture.large"
         :firstName="user.name.first"
         :lastName="user.name.last"
         :dob="user.dob.age"
         :city="user.location.city"
         :state="user.location.state"
      />
    
  </b-container>
</template>



<script>
import axios from "axios";
import UsersCard from '../components/UsersCard.vue'

export default {
    components: {
        UsersCard
    },
    data() {
    return {
      title: "Users",
      users: [],
    };
  },
  //head method for Seo
    head() {
      return {
        meta: [
          // hid is used as unique identifier. Do not use `vmid` for it as it will not work
          {
            hid: 'User',
            name: 'User Page',
            content: 'User content'
          }
        ]
      }
    },
   methods: {
    formatDate(dateString) {
      let convertedDate = new Date(dateString);
      return convertedDate.toDateString();
    },
    getInitialUsers() {
      axios.get(`https://randomuser.me/api/?results=5`).then((response) => {
        this.users = response.data.results;
      });
    },
    getNextUser() {
      window.onscroll = () => {
        let bottomOfWindow = document.documentElement.scrollHeight - document.documentElement.scrollTop === document.documentElement.clientHeight;
        if (bottomOfWindow) {
          axios.get(`https://randomuser.me/api/?results=25`).then(response => {
             this.users.push(response.data.results[0])
          });
        }
      }
    }
  },
  beforeMount() {
    this.getInitialUsers();
  },
  mounted() {
    this.getNextUser();
  }
}

</script>

<style>
.user {
  display: flex;
  background: #ccc;
  border-radius: 1em;
  margin: 1em auto;
}

.user-avatar {
  padding: 1em;
}

.user-avatar img {
  display: block;
  width: 100%;
  min-width: 64px;
  height: auto;
  border-radius: 50%;
}

.user-details {
  padding: 1em;
}

.user-name {
  margin: 0;
  padding: 0;
  font-size: 2rem;
  font-weight: 900;
}
</style>