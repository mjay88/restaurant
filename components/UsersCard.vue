<template>
    <div class="users-card">
        <div class="user-avatar">
            <img :src="imgSrc">
        </div>
        <div class="user-details">
            <h2 class="user-name">
            {{ firstName }}
            {{ lastName }}
            </h2>
            <ul>
            <li><strong>Birthday:</strong> {{ formatDate(dob) }}</li>
            <li><strong>Location:</strong> {{ city }}, {{ state }}</li>
            </ul>
        </div>
    </div>
</template>

<script>
import axios from "axios";


export default {
    //register component
    name: "UsersCard",
    //validation
	props: {
		imgSrc: String,
        firstName: String,
        lastName: String,
        city: String,
        state: String,
        dob: Number
	},
    methods:{
         formatDate(dateString) {
        let convertedDate = new Date(dateString);
        return convertedDate.toDateString();
        }
       
    }
  
    
}
</script>