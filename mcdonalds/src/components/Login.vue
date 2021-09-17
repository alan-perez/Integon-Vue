<template>
<div>
    <h1>Login</h1>
 <input type="text" placeholder="usuario" v-model="userName">
 <br>
  <input type="text" placeholder="contraseña" v-model="password">
  <input type="button" value="Login" @click="logOn()">
</div>
 
  

</template>

<script>
export default {
    data(){
        return{
            userName:'',
            password:'',
            adminUser:'admin',
            adminPass:'pass'
        }
    },
    methods:{
        logOn:function(){
            if(this.userName == this.adminUser && this.password == this.adminPass)
             this.$router.push({
                 name:'Home',
                 params:{logonSuccesfull:true}
                 });
            // console.log(`trying yo logon using ${this.username} and ${this.password}`);
        }
        },
    }

</script>

<style>

</style>