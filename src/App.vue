<template>
  <div id="app" class="hh">
    <nav>
      <div class="navigation">
        <div>
          <router-link
            class="main"
            :class="{ activeMain: this.$store.state.activeMain }"
            to="/"
            >Главная страница</router-link
          >
          <router-link
            class="main"
            :class="{ activeSearch: this.$store.state.activeSearch }"
            to="/SearchUser"
            >Поиск</router-link
          >
          <router-link
            class="main"
            :class="{ activeInfo: this.$store.state.activeInfo }"
            to="/Info"
            >Информация</router-link
          >
        </div>
      </div>
    </nav>
    <router-view></router-view>
  </div>
</template>

<!-- SCRIPTS -->
<script>
import ListUser from "./components/ListUser.vue";
import SearchUser from "./components/SearchUser.vue";

export default {
  components: {
    ListUser,
    SearchUser,
  },
  name: "App",
  data() {
    return {};
  },
  mounted() {
    this.getdata();
  },
  methods: {
    async getdata() {
      //парсим данные
      const res = await fetch("https://jsonplaceholder.typicode.com/users");
      const json = await res.json();
      this.$store.state.data = json; //записываем данные в массив из vuex
      console.log(this.$store.state.data); //выводим массив из store(vuex)
    },
  },
};
</script>

<style>
.main {
  border: 1px solid black;
  padding: 10px 15px;
  text-decoration: none;
  color: black;
}
.navigation {
  margin: 20px 0 50px;
  display: flex;
  justify-content: space-between;
}
.main:hover {
  background-color: rgb(123, 120, 120);
}
.activeSearch {
  border: 1px solid black;
  padding: 10px 15px;
  text-decoration: none;
  color: black;
  background-color: rgb(123, 120, 120);
}
.activeMain {
  border: 1px solid black;
  padding: 10px 15px;
  text-decoration: none;
  color: black;
  background-color: rgb(123, 120, 120);
}
.activeInfo {
  border: 1px solid black;
  padding: 10px 15px;
  text-decoration: none;
  color: black;
  background-color: rgb(123, 120, 120);
}
.info1 {
  border: 1px solid black;
  padding: 10px 15px;
  text-decoration: none;
  color: black;
}
.info1:hover {
  background-color: rgb(123, 120, 120);
}
body {
  background-color: rgb(194, 194, 189);
}
p {
  font-weight: 600;
}
a {
  font-weight: 600;
}
</style>
