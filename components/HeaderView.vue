<template>
    <div id="hed">
        <!-- the site's general header and nav bar -->
        <header class="hed">
        <div class="hed__container">
            <h1 class="hed__title">BAKER'S HOME</h1>
            <h2 class="hed__subtitle">helping you rise from your desk</h2>
        </div>
        <b-navbar toggleable="md" class="hed__nav" >
            <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>
            <b-collapse id="nav-collapse" is-nav> 
                <b-navbar-nav class="hed__navbar">
                    <b-nav-item><nuxt-link class="hed__navlink" to="/">Home</nuxt-link></b-nav-item>
                    <b-nav-item><nuxt-link class="hed__navlink" to="/recipes">Recipes</nuxt-link></b-nav-item>
                    <b-nav-item><nuxt-link class="hed__navlink" to="/community">Community</nuxt-link></b-nav-item>
                    <b-nav-item><nuxt-link class="hed__navlink" to="/faq">FAQ</nuxt-link></b-nav-item>
                </b-navbar-nav>
            </b-collapse> 
            <!-- login button using slot -->
            <div class=" hed__navlogin">
                <LoginButton>Login</LoginButton>
            </div>

        </b-navbar>
        </header>
    </div>  
</template>

<script >
// import and name LoginButton
import LoginButton from "./LoginButton.vue";

  export default {
    components: {
      LoginButton
    }
  }
</script>