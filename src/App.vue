
import "./App.css";

function App() {
  <template>
  <div class="mainContainer">
    <h1 class="titleTable">IronContacts</h1>
    <button @click="randomContact">Add Random Contact</button>
   <table class="tble">
    <tr class="headerTable">
      <td>Picture</td>
      <td>Name</td>
      <td>Popularity</td>
      <td>Won Oscar</td>
      <td>Won Emmy</td>
    </tr>
    <tr class="singleColumns" v-for="contact in contacts.slice(0, 9)" :key="contact.id">
      <td><img class="pictures" :src="contact.pictureUrl" alt=""></td>
      <td>{{ contact.name }}</td>
      <td>{{ contact.popularity.toFixed(2) }}</td>
      <td><span v-if="contact.wonOscar">🏆</span></td>
      <td><span v-if="contact.wonEmmy">🏆</span></td>
    </tr>
   </table>
  </div>
</template>
<script>
  import contacts from "./contacts.json";

  export default {
    data() {
      return {
        contacts: contacts,

      };
    },
    computed: {
      getListContacts() {
        return this.contacts.map((element) => {
          return {
            contact: element,
          
          };
        });
      },
    },
    methods: {
      randomContact() {
        if(this.contacts.length > 0) {
          const contactsRandom = Math.floor(Math.random() * this.contacts.length);
          const arrayRandom = this.contacts[contactsRandom];
          return arrayRandom;
        }

      }
      }
  }
</script>
<style>
.pictures{
  height: 150px;
  width: auto;
}


.headerTable {
  font-weight: bold;
  font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
}
.titleTable{
  font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
}
.mainContainer {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.tble{
  justify-content: center;
}
.singleColumns{
  text-align: center;
}

</style>
}
export default App;
