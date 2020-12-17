<template>
    <div id="UserBalance">
      <!--  <section class="login__container">
            <h2 class="title">Documentos</h2>
            <form class="login__container--form">
                <div class="document-select">
                  <input class="textfield" type="text" placeholder="texto" v-model="input">
                    
                </div>
                <div class="document-select">
                  <button type="submit" class="button" v-on:click="busqueda"  >Buscar</button>                 
                </div>
                <div class="document-select">                 
               
                </div>
              
            </form>
        </section> -->
       <section class="login__container">
        <h2 class="title">Documentos</h2>
        <form class="login__container--form">
          <div class="document-select">
            <label>
              <input type="radio" name="docs" id="cbox1">Documento Médico
            </label>
          </div>
          <div class="document-select">
            <label>
              <input type="radio" name="docs" id="cbox1">Documento Legal
            </label>
          </div>
          <div class="document-select">
            <label>
              <input type="radio" name="docs" id="cbox1">Documento Financiero
            </label>
				  </div>
          
				<button  class="button" v-on:click="getResultado" >Buscar</button>
        <button type="submit" class="button" v-on:click="getBalance" > Verificar vigencia</button>
				
			</form>


      </section>
                        
    </div>
</template>

<script>
  import axios from 'axios';
  export default {
    name: 'UserBalance',
    methods: {
      busqueda: function(){
        alert("Hola mundo");      
      },
    
     getResultado: function(){
    if(this.$route.name != "resultado"){
      let username = localStorage.getItem("current_username")
      this.$router.push({ name:"resultado",
      params:{username:username}
    }) 
  }
},
},

    created: function(){
    this.username = this.$route.params.username
    let self = this
    axios.get("http://127.0.0.1:8000/user/balance/" + this.username)
    .then((result) => {
    self.balance = result.data.balance
    })
    .catch((error) => {
    alert("ERROR Servidor");
    });
    }
  }
</script>
<style>
#UserBalance{
width: 100%;
height: 100%;
display: flex;
flex-direction: column;
justify-content: center;
align-items: center;
}
#UserBalance h2{
font-size: 50px;
color: #283747;
}
#UserBalance span{
color: crimson;
font-weight: bold;
}
body{
  margin: 0 0 0 0;
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
  padding-left: 45px;

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
   padding-left: 45px;

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
  width: 200px;
  align-items: center;

}
div .main-component .button button:hover {
  background: #E5E7E9;
  border: 1px solid #E5E7E9;

}
input .textfield{

  padding: 5px 5px 5px 5px;
}

</style>
