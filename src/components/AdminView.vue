<template>
  <div class="admin-view">
    <div class="form-group">
      <label for="title">URL</label>
      <input id="title" v-model="title" class="admin-input" />
    </div>
    <button @click="handleSubmit" class="admin-button">SUBMIT</button>
  </div>
</template>

<script>
export default {
  name: "AdminView",
  data() {
    return {
      title: "",
      image: "",
      description: "",
    };
  },
  methods: {
    handleSubmit() {
      this.$emit("createProject", {
        title: this.title,
        image: this.image,
        description: this.description,
      });
    },
  },
};
</script>

<style scoped>
.admin-view {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.form-group {
  display: flex;
  flex-direction: row;
  align-items: center;
  margin-bottom: 10px;
}

.form-group label {
  font-family: "Josefin Sans", sans-serif;
  /* Estilos adicionales para la etiqueta */
  margin-right: 10px;
}

.admin-input {
  font-family: "Josefin Sans", sans-serif;
  /* Estilos adicionales para el input */
  width: 300px;
  height: 30px;
  font-size: 18px;
}

.admin-button {
  font-family: "Josefin Sans", sans-serif;
  /* Estilos adicionales para el botón */
  width: 120px;
  height: 40px;
  font-size: 18px;
}
</style>
