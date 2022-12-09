<template>

<header >
  <h1>Mi carrito de contactos</h1>
</header>

<body>

  <button @click="add()">Agregar un nuevo contacto</button>
  <button @click="sortAbc()">Ordenar Alfabeticamente </button>
  <button @click="sortPop()">Ordenar por popularidad</button>

  <table>
    <thead>
      <tr>
        <th>*</th>
        <th>Foto</th>
        <th>Nombre</th>
        <th>Popularidad</th>
        <th>Won an Oscar</th>
        <th>Won an EMY</th>
        <th>Action</th>
      </tr>    
    </thead>

    <tbody>
      <tr v-for="(contact, index) in contacts">
        <th>{{(index+1)}}</th>         
        <th><img width="50" :src="contact.pictureUrl" alt="foto de perfil"></th>
        <th>{{ contact.name }}</th>
        <th>{{ contact.popularity }} </th>
        <th> 
          <img v-if="(contact.wonOscar === true)" src="../public/trophy.png" alt="Trophy" width="20">
        </th> 
        <th>
          <img v-if="(contact.wonEmmy === true)" src="../public/trophy.png" alt="Trophy" width="20">
        </th>
        <th>
          <button @click="borrar(index)">Delete</button>
        </th>
      </tr>
    </tbody>
 </table>
  
</body>
</template>

<script>
import CONTACTS from "./contacts.json";

export default{
  computed:{  
  },

  data(){
    return{
      contacts:CONTACTS.slice(0,5),
    };
  },

  methods:{ 
    add(){      
      let newContact =CONTACTS[Math.floor(Math.random()*CONTACTS.length)]; 
      if (this.contacts.includes(newContact) === false) {
        return this.contacts.push(newContact);
      }
      else{
        this.add()
      }
    },

    borrar(num){
      return this.contacts.splice(num,1);
    },

    sortPop(){
      return this.contacts.sort(function(a, b) {
          let keyA = a.popularity;
          let keyB = b.popularity;          
          if (keyA < keyB) {
            return 1;              
            }
          if (keyA > keyB){
          return -1;
          } 
          return 0;
      });
    },

    sortAbc(){
        return this.contacts.sort(function(a, b) {
        let keyA = a.name;
        let keyB = b.name;  
         if (keyA < keyB) {
        return -1;
         }
        if (keyA > keyB){
        return 1;
         }
        return 0;
        });
    },

  }, 

};
</script>

<style scoped>
  button{
    border: solid 1px black;
    padding: 6px;
    margin: 5px;
  }
  body {
    text-align: center;
  }
  header{
    text-align: center;
    font-size: 50px;
  }
  table{
    margin: auto;
    margin-top: 50px;
  }
  th {
    padding: 7px;
  }
</style>
