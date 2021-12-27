<template>
        <ul id="footer" class="footer nav navbar-dark postion-absolute">  
                  <NuxtLink class="nav-link" to="/">Home</NuxtLink>
                  <NuxtLink class="nav-link" to="/catering">Catering</NuxtLink>
                  <NuxtLink class="nav-link" to="/checkout">Checkout</NuxtLink>
        </ul>        
</template>

<script>

export default {
  name: 'Footer',
  data: () => ({
   
    
  }) 
  
}


</script>
<style>
/*bootstrap styling not applying?*/
.footer{
  width: 100%;
  text-decoration: none;
  position: absolute;
  bottom: 0;

}
 .nav-link {
  text-decoration: none;
   color: #424242;
}
.nav-link:focus, .nav-link:hover {
    color: #424242;
}
</style>