<template>
  <div id="app">
    <div class="header">
      <div class="header-left">
        <img src="./img/lupa.png" width="80px" alt="">
        <h1>Tracker</h1>
      </div>      
            
        <nav>
          <button v-on:click="init" v-if="is_auth"> Inicio </button>
          <button v-on:click="getBalance" v-if="is_auth" > Documentos </button>  
          <button v-on:click="getBalance" v-if="is_auth" > Documentos </button>  
     
        </nav>
      
    </div>
    
    <div class="main-component">   
 
    <router-view> </router-view>
    

    </div>
  
    
    <div class="footer">
      <h2>Misión TIC 2022</h2>
    </div>

  </div>
</template>

<script>

//import vueRouter from 'vue-router'

export default {
  name: 'App',
  components: {},

//methods:{
    /*updateAuth: function(){
      var self = this
      self.is_auth  = localStorage.getItem('isAuth') || false

      if(self.is_auth == false)
        self.$router.push({name: "user_auth"})

      else{
        let username = localStorage.getItem("current_username")
        self.$router.push({name: "user", params:{ username: username }})
      }  
    },*/




  data: function(){
    return {
      is_auth: localStorage.getItem('isAuth') || false ,
      base_datos : [{doc_Name: "Historia Clinica",field: "Documento Médico", author:"Marisol", expiration:"2019-12-15"},
                    {doc_Name: "Camara y comercio",field: "Documento Legal", author:"Luis", expiration:"2020-12-20"},
                    {doc_Name: "Certificacion Bancaria",field: "Documento Economia", author:"Juan", expiration:"2021-6-17"} ]
      
      }

  },
  methods: {

    init: function(){
    if(this.$route.name != "user"){
      let username = localStorage.getItem("current_username")
      this.$router.push({name: "user", params:{username:username}})
    }
    },
    getBalance: function(){
    if(this.$route.name != "user_balance"){
      let username = localStorage.getItem("current_username")
      this.$router.push({ name:"user_balance",
      params:{username:username}
    })}},
    


  },
  beforeCreate: function(){
    localStorage.setItem('current_username', 'Sebastian')
    localStorage.setItem('isAuth', true)
    this.$router.push({name:"user",params:{username:'camilo24'}})
    }
}

</script>

<style>

body{
  margin: 0 0 0 0;
 
}
.normal{
  padding: 225px;
   background: linear-gradient(#21C08B, #6930C3);
}
.header{
  margin: 0%;
  padding: 0;
  width: 100%;
  height: 10vh;
  min-height: 100px;
  background-color: #283747 ;
  color:#E5E7E9 ;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.header h1{
  width: 20%;
  text-align: center;
}
.header nav {
  height: 100%;
  width: 45%;
  display: flex;
  justify-content: space-around;
  align-items: center;
  font-size: 20px;
}

.header nav button{
  color: #E5E7E9;
  background: #283747;
  border: 1px solid #E5E7E9;
  border-radius: 5px;
  padding: 10px 20px;
  cursor: pointer;
}
.header nav button:hover{
  color: #283747;
  background: #E5E7E9;
  border: 1px solid #E5E7E9;
}

.main-component{
  height: 75vh;
  margin: 0%;
  padding: 0%;
  background: #FDFEFE ;
}
.footer{
  margin: 0;
  padding: 0;
  width: 100%;
  height: 10vh;
  min-height: 0px;
  background-color: #283747;
  color: #E5E7E9;
}
.footer h2{
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.login__container {
	background-color: rgba(255, 255, 255, 0.1);
	border: none;
	border-radius: 40px;
	color: white;
	padding: 10px 10px 10px;
	min-height: 300px;
	width: 300px;
	display: flex;
	justify-content: space-around;
	flex-direction:column; 
}
.title {

text-align: center;
font-size: 35px;

}
.login__container--form{
 	display: flex;
 	flex-direction: column;

}
.main-component {
	background: linear-gradient(#21C08B, #6930C3);
	display: flex;
	align-items: center;
	justify-content: center;
	flex-direction: column;
	padding: 0px 30px;
	min-height: calc(100vh - 400px);
}
h2 {
  margin: 0;
}

.document-select{
	color: white;
	display: flex;
	justify-content: space-between;
  margin: 10px;
  padding-bottom: 10px;
  
}
.document-select label input{
  margin-right: 15px;
  
}
.login__container--form{
 	display: flex;
   flex-direction: column;
   padding: 10px;

}
.login__container--form label{
    font-size: 20px;
}
.button {
	background-color: rgba(255, 255, 255, 0.1);
	border: none;
	border-radius: 25px;
	color: white;
	cursor: pointer;
	font-size: 16px;
	font-weight: bold;
 	font-family: "Muli", sans-serif;
 	height: 50px;
 	letter-spacing: 1px;
 	margin: 10px 0px;

}
div .main-component .button button:hover {
  background: #E5E7E9;
  border: 1px solid #E5E7E9;

}
.header-left{
  display: flex;
  padding: 15px;
}
.header-left h1{
  padding: 5px;
  }
.header-rigth{
  display:flex;
  align-items: center;

}
nav {
  display: none;
}

</style>
