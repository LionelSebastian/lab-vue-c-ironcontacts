<template>
    <table>
      <thead>
        <tr>
          <th>Foto</th>
          <th>Nombre</th>
          <th>Popularidad</th>
          <th>Won an Oscar</th>
          <th>Won an EMY</th>
        </tr>    
      </thead>
      <tbody>
        <tr v-for="contact in contacts">         
          <th><img width="50" :src="contact.pictureUrl" alt="foto de perfil"></th>
          <th>{{ contact.name }}</th>
          <th>{{ contact.popularity }} </th>
          <th> <img v-if="item." src="./" alt=""></th>
        </tr>
      </tbody>
   </table>
</template>

<script>
import CONTACTS from "./contacts.json";

export default{
  components:{

  },
  data(){
    return{
      contacts:CONTACTS.slice(0,5),
    };
  },
};
</script>

<style>

</style>
