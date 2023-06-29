<template>
  <div>
    <h1>Hello World</h1>

    <button @click="showUserView" :class="{ active: activeView === 'User' }">
      User
    </button>
    <button @click="showAdminView" :class="{ active: activeView === 'Admin' }">
      Admin
    </button>

    <component :is="activeView"></component>
    <admin-view v-if="isAdmin" @createProject="addProject" />
    <user-view v-else />
  </div>
</template>

<script>
import AdminView from "./components/AdminView.vue";
import UserView from "./components/UserView.vue";

export default {
  components: {
    User,
    Admin,
  },
  data() {
    return {
      activeView: "User",
    };
  },
  methods: {
    showUserView() {
      this.activeView = "User";
    },
    showAdminView() {
      this.activeView = "Admin";
    },
  },
};
</script>
<style>
button {
  padding: 10px 20px;
  background-color: #ccc;
  color: #fff;
  border: none;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

button.active {
  background-color: #333;
}
</style>
