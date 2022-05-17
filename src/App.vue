<template>
  <body>
    <div id="app">
      <div class="header">
      <h1 style="text-align: left">Welcome to Opportunity</h1>
      <p class="currentTime">{{ currentDateTime() }}</p>
    </div>
    
    <ul class="unorderedList">
      <li class="li">
        <span class="entry-daytime">12.00 Uhr</span>
        <h3>Basisbeschäftigung Besuch</h3>
        <span class="entry-description">erster Eintrag </span>
      </li>
      
      <li class="li">
        <span class="entry-daytime">14.00 Uhr </span>
        <h3>Basisbeschäftigung Besuch 2</h3>
        <span class="entry-description">nächster Eintrag </span>
      </li>
    
      <li class="li">
        <span class="entry-daytime">16.00 Uhr</span>
        <h3>Basisbeschäftigung Besuch X</h3>
        <span class="entry-description">letzter Eintrag</span>
      </li>
    </ul>

    <footer class="footer">
      <img class="img" src="./assets/STZH_SEB_Logo.png"
      />
      <img class="img" src="./assets/Opportunity.png"
      />
      <img class="img" src="./assets/SAG_Logo_De.png"
      />
    </footer>
  
    </div>
  </body>
</template>

<script>
import axios from "axios";

export default {
  name: "App",
  data() {
  sheet_id: "1a81aI0Y8ViZO0tI92h2YSMqVQJ8hmNNMyMylXgvwiU4",
  api_token: "AIzaSyA-qeDXOhEeQDA0vQf7LgkF7DQtGnAtmAU",
  entries: [],
  currentDate: "",
  },
  computed = {
    gsheet_url() {
      return 'https'
    }
  }


  function() {
    return `https://sheets.googleapis.com/v4/spreadsheets/${this.sheet_id}/values:batchGet?ranges=A1%3AE100&valueRenderOption=FORMATTED_VALUE&key=${this.api_token}`;
    },

  methods: {
    getData() {
      axios.get(this.gsheet_url).then((response) => )
      this.entries = ''
    }
    currentDateTime() {
      const current = new Date();
      const date =
        current.getDate() +
        "." +
        (current.getMonth() + 1) +
        "." +
        current.getFullYear();
      return date;
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@400;500;700;900&display=swap");
body {
  margin: 0;
  font-family: 'Inter', Helvetica, sans-serif;
  background-position: center;
  background-size: cover;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding-top: 20px;
  background-color: #FFFFFF;
  min-height: 10vh;
  font-size: 28px;
  line-height: 36px;
}

.li {
  list-style-type: none;
  background-color: #0F05A0;
  color:#ffbfab;
  margin: 2rem;
  padding: 2rem; 
}

.unorderedList{
  line-height: 1rem;
  margin-right: 10rem;
}

.entry-daytime {
  color: #EB5E00;
  font-weight: 900;
}

.header {
  margin-left: 4.5rem;
  margin-right: 10rem;
  text-align: left;
  font-size: big;
  line-height: 2em;
  }

.currentTime{
  font-size: 30px;
  font-weight: 900;
}

.img{
  width: 20%;
}

footer{
  display: flex;
  align-content: bottom;
  padding-bottom: 10px;
  background-color: #ffffff;
}

</style>

