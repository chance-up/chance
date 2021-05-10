<template>
  <div class="hello">
    <div class="g-signin2" id="google-signin-btn" data-onsuccess="onSignIn"></div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  created(){
    window.onSignIn = this.onSignIn;
  },
  methods:{
    onSignIn(googleUser){
      const profile = googleUser.getBasicProfile();
      console.log('ID Token: ', googleUser.getAuthResponse().id_token); // 실제 토큰
      console.log('ID: ' + profile.getId()); // Do not send to your backend! Use an ID token instead.
      console.log('Name: ' + profile.getName());
      console.log('Image URL: ' + profile.getImageUrl());
      console.log('Email: ' + profile.getEmail()); // This is null if the 'email' scope is not present.
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
