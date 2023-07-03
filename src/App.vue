<template>
  <div class="container">
    <h1>hello there!</h1>
    <div class="button-container">
      <button
        :class="{ button: true, 'highligted-button': isAdmin }"
        @click="($event) => (isAdmin = true)"
      >
        admin
      </button>
      <button
        :class="{ button: true, 'highligted-button': !isAdmin }"
        @click="($event) => (isAdmin = false)"
      >
        user
      </button>
      <admin-view v-if="isAdmin" @createProject="addProject" />
      <user-view v-else />
    </div>
  </div>
</template>

<script>
import AdminView from "./components/AdminView.vue";
import UserView from "./components/UserView.vue";

export default {
  name: "app",
  components: {
    userView: UserView,
    adminView: AdminView,
  },
  data() {
    return {
      isAdmin: true,
      allProjects: [],
    };
  },
  methods: {
    addProject(project) {
      this.allProjects.push(project);
    },
  },
};
</script>

<style>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
}

.container::before {
  content: "";
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 400px;
  height: 400px;
  border-radius: 50%;
  background-color: #5a9367;
  opacity: 1; /* Establece la opacidad inicial en 1 */
  animation: fadeCircle 10s linear infinite; /* Agrega una animación de opacidad con duración de 2 segundos y repetición infinita */
  z-index: -1; /* Coloca el círculo detrás del contenido estableciendo un valor de z-index negativo */
}

.container:click::before {
  animation: none; /* Detiene la animación al hacer hover en el contenedor */
  opacity: 0; /* Establece la opacidad en 0 */
}

@keyframes fadeCircle {
  0% {
    opacity: 0.1; /* Opacidad inicial en 1 */
  }
  25% {
    opacity: 0.5; /* Opacidad en 0 a la mitad de la animación */
  }
  50% {
    opacity: 1; /* Opacidad en 0 a la mitad de la animación */
  }
  25% {
    opacity: 0.5; /* Opacidad en 0 a la mitad de la animación */
  }
  100% {
    opacity: 0.1; /* Opacidad final en 1 */
  }
}

.button-container {
  display: inline-block;
}
.button {
  background-color: rgb(246, 235, 204);
  font-family: "Josefin Sans";
  font-size: 18px;
  border-radius: 5px;
  margin: 6px;
  margin-bottom: 15px;
  width: 80px;
  height: 28px;
  border: none;
}

.highligted-button {
  background-color: rgb(135, 0, 0);
  color: rgb(255, 255, 255);
  border: none;
}
h1 {
  color: white;
}
</style>
