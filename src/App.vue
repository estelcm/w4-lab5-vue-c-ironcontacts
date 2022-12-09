// src/App.vue
<template>

<h1>IronContacts</h1>


  <table>
    <thead>
      <tr>
        <th>Picture </th>
        <th>Name</th>
        <th>Popularity </th>
        <th>Won an Oscar</th>
        <th>Won anEmmy</th>
        <th>Actions</th>
        

      </tr>
    </thead>
    <tbody>
      <tr v-for="(contact, index) in contactList" :key="index" >
        <td> <img :src="contact.pictureUrl" :alt="contact.pictureUrl" width="70"/> </td>
         <td>{{ contact.name }}</td> 
          <td>{{ contact.popularity }}</td>
          <td v-if="(contact.wonOscar===true )"><i class="fas fa-trophy"></i></td>
          <td v-if="(contact.wonEmmy===true )"><i class="fas fa-trophy"></i></td>
          <td>  <button @click="deleteElement(index)" type="button">
              <i class="fa-solid fa-trash"></i></button></td>
      </tr>
      <button @click="newRandomContact">Add Random Contact</button>
    </tbody>
  </table>
</template>

<script>
import contacts from "./contacts.json";
export default {
  data() {
    return {
      contacts: contacts,
      contactList: contacts.slice(0,5),
    };
  },

  methods:{
    deleteElement(index){
      this.contactList.splice(index,1);
    },
  
newRandomContact(){

const randomContact =Math.floor(Math.random() * contacts.length);

if(!this.contactList.includes(contacts[randomContact])){
this.contactList.push(contacts[randomContact]);
 }
return newRandomContact;
}

  },
 
    
  //     const contactLength = this.contacts.length;
  //   function randomIntFromInterval(6, contactLength ) { // min and max included 
  // return Math.floor(Math.random() * (contactLenght - 6 + 1) + 6)};

  
//  methods:{
//   contactList(contact){
//     contactList.slice(0,5);
//   }
//  }
};
</script>

<style></style>
