<template>
  <div id="app">
    <div class="user" v-for="users of this.$store.state.data" :key="users.id">
      <div class="block">
        <p class="oneuser">{{ users.name }}</p>
        <button class="info" @click="getInfo(users.id)">+</button>
      </div>
      <div v-if="IdUser == users.id">
        <div class="hidein" v-if="hidden">
          <button class="hideInfo" @click="hideInfo">-</button>
        </div>
        <p class="oneuser">{{ users.username }}</p>
        <p class="oneuser">{{ users.email }}</p>
        <p class="oneuser">{{ users.phone }}</p>
      </div>
    </div>
    <router-view />
  </div>
</template>

<script>
export default {
  data() {
    return {
      IdUser: 0,
      hidden: 0,
    };
  },
  mounted() {
    this.$store.state.activeMain = 1;
    this.$store.state.activeInfo = 0;
    this.$store.state.activeSearch = 0;
  },
  methods: {
    getInfo(id) {
      this.IdUser = id;
      this.hidden = 1;
    },
    hideInfo() {
      this.IdUser = 0;
    },
  },
};
</script>
<style>
.user {
  display: block;
  border: 1px solid;
  margin-bottom: 10px;
  border-radius: 15px;
  width: 300px;
  margin: 0 auto 10px;
}
.info {
  height: 20px;
  border-radius: 50%;
  margin-right: 10px;
}
.oneuser {
  margin-left: 10px;
}
.block {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.hideInfo {
  height: 20px;
  border-radius: 50%;
  margin-right: 10px;
  position: absolute;
  top: -35px;
  right: 0px;
  z-index: 50;
  width: 24px;
}
.hidein {
  display: flex;
  justify-content: space-between;
  align-items: center;
  position: relative;
}
</style>
