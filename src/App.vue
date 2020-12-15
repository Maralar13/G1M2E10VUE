<template>
  <div id="app">
    <div class="header">
      <h1>Tracker</h1>
      <nav>
        <button > Inicio </button>
        <button v-if="is_auth" > Descargas </button>
        <button v-if="is_auth" >Cerrar Sesión</button>
      </nav>
    </div>
    <div class="main-component">
      <section class="login__container">
        <h2 class="title">Documentos</h2>
        <form class="login__container--form">
          <div class="document-select">
            <label>
              <input type="checkbox" name="" id="cbox1" value="checkbox">Documento Médico
            </label>
          </div>
          <div class="document-select">
            <label>
              <input type="checkbox" name="" id="cbox1" value="checkbox">Documento Legal
            </label>
          </div>
          <div class="document-select">
            <label>
              <input type="checkbox" name="" id="cbox1" value="checkbox">Documento Financiero
            </label>
				  </div>
          
				<button class="button" v-on:click="init" v-if="is_auth" >Buscar</button>
        <button class="button" v-on:click="getBalance" v-if="is_auth"> Verificar vigencia</button>
				
			</form>


      </section>





      
    </div>
    <div class="footer">
      <h2>Misión TIC 2022</h2>
    </div>

  </div>
</template>

<script>
export default {
  name: 'App',
  components: {},
  data: function(){
    return {
      is_auth: localStorage.getItem('isAuth') || false
      }
  },
  methods: {
  },
  beforeCreate: function(){
    localStorage.setItem('current_username', 'camilo24')
    localStorage.setItem('isAuth', true)
    }
}

</script>

<style>

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

</style>
