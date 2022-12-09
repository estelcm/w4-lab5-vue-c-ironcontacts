// src/App.vue
<template>
  <h1>IronContacts</h1>

  <table>
    <thead>
      <div class="botones">
        <button @click="newRandomContact">Add Random Contact</button>
        <button @click="popularity">Sort by popularity</button>
        <button @click="sortedByName">Sort by name</button>
      </div>
      <tr>
        <th>Picture</th>
        <th>Name</th>
        <th>Popularity</th>
        <th>Won an Oscar</th>
        <th>Won an Emmy</th>
        <th>Actions</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(contact, index) in contactList" :key="index">
        <td >
          <img :src="contact.pictureUrl" :alt="contact.pictureUrl" width="70" />
        </td>
        <td>{{ contact.name }}</td>
        <td>{{ contact.popularity }}</td>
        <td v-if="contact.wonOscar === true"><i class="fas fa-trophy"></i></td>
        <td v-if="contact.wonEmmy === true"><i class="fas fa-trophy"></i></td>
        <td>
          <button @click="deleteElement(index)" type="button">
            <i class="fa-solid fa-trash"></i>
          </button>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script>
import contacts from "./contacts.json";
export default {
  data() {
    return {
      contacts: contacts,
      contactList: contacts.slice(0, 5),
    };
  },

  methods: {
    deleteElement(index) {
      this.contactList.splice(index, 1);
    },

    newRandomContact() {
      const randomContact = Math.floor(Math.random() * contacts.length);

      if (!this.contactList.includes(contacts[randomContact])) {
        this.contactList.push(contacts[randomContact]);
      }
      return newRandomContact;
    },

    sortedByName() {
    this.contactList.sort(function (a, b) {
      if (b.name > a.name)return -1;
      if (a.name > b.name) return 1;
   });
    //   console.log("eeeeeeppppaaaa" + popularity);
    },
    popularity(){
      // const popular= this.contactList.popularity
      this.contactList.sort(function (a, b) {
return b.popularity-a.popularity;

      });

    }
 
  },
};
</script>

<style scoped>
/* .botones {
  display: flex;
  justify-content: space-around; */
/* } */
h1 {
  text-align: center;
}

</style>
