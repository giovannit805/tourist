<template>
  <div class="navigation-logged">
      <nav class="navbar navbar-expand-lg navbar-dark" style="background-color:rgb(235, 141, 134)">
    <div class="container-fluid">
    <router-link class="navbar-brand" :to="{name:'Landing'}">
      <img src="../assets/logos/we-travel/letter-logo-md.png" alt="" class="d-inline-block align-text-top brand-img-nav">
    </router-link>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarText" aria-controls="navbarText" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarText">
      <ul class="navbar-nav me-auto mb-2 mb-lg-0">
        <li class="nav-item">
          <router-link class="nav-link active" aria-current="page" :to="{name:'Home'}">Home</router-link>
         </li>
         <li class="nav-item">
          <router-link class="nav-link" :to="{name:'Discover'}">Discover</router-link>
         </li> 
        <li class="nav-item">
          <router-link class="nav-link" :to="{name:'About'}">About</router-link>
         </li>
          <li class="nav-item">
           <router-link class="nav-link" :to="{path:`/profile/${getRouteSlug}`}">My Profile</router-link>
         </li>
         <li class="nav-item">
          <router-link class="nav-link" :to="{name:'Account'}">My Account</router-link>
         </li>
<!--Added the messaging nav link to nav bar.-->
         <li class="nav-item">
          <router-link class="nav-link" :to="{name:'Messaging'}">Messaging</router-link>
         </li>
         <li class="nav-item">
          <router-link class="nav-link  " :to="{name:'Requests'}">
            Requests
             <span class="badge rounded-pill bg-secondary">{{this.$store.state.reservations.pending.length}}</span>
            
             
          </router-link>
         </li>
      </ul>
      <span class="navbar-text">
          Welcome back {{getUser}}!
      </span>
      <button @click="logOut()" class="btn btn-primary log-out"><span v-if="small">Log Out </span><i class="fa fa-sign-out"></i></button>
    </div>
  </div>
</nav>
  </div>
</template>

<script>

import NavbarLogged from '../components/NavbarLogged'

 export default {
  components:{NavbarLogged},
  data(){
    return{
      small:true
    }
  },
  methods:{
    logOut(){
      this.$store.commit('logoutUser');
      this.$router.push({name:'Home'})
    }
  },
  computed:{
    getRouteSlug(){
      return this.$store.state.slug
    },
    isLogged(){
      let status = this.$store.state.loggedIn;
      return status;
    },
    getUser(){
      let user = this.$store.state.fullName;
      return user;
    }
  }
}
</script>

<style>
.log-out{
  margin-left:20px;
  background-color:rgb(34, 177, 221);
  border-color:rgb(34, 177, 221);
}
.navbar-dark .navbar-nav .nav-link{
  font-size:1.2em !important;
}
.brand-img-nav{
    height:40px !important;
    width:auto;
}
.navigation-logged{
     box-shadow:5px 5px 20px 5px rgba(19, 19, 19, 0.562);

}
</style>