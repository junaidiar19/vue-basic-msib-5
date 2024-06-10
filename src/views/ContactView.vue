<template>
  <div class="d-block">
    <button class="btn btn-light mb-3" @click="count++">
      Click {{ count }}
    </button>
    <div class="d-flex mb-3">
      <input
        :type="!password ? 'password' : 'text'"
        class="form-control me-1"
        value="Password"
      />
      <button class="btn btn-light" @click="showPassword">Show</button>
      <!-- <span v-if="password">Show Password</span>
      <span v-else>Hide Password</span> -->
    </div>
    <div class="mb-3">
      <h6>Todo List</h6>
      <ul>
        <li v-for="todo in todos" :key="todo.id">{{ todo.text }}</li>
      </ul>
    </div>
    <div class="mb-3">
      <h6>Formulir</h6>
      <form @submit="submit">
        <div class="mb-3">
          <label>Nama Lengkap</label>
          <input
            type="text"
            class="form-control"
            placeholder="Masukan nama Anda..."
            v-model="form.name"
          />
        </div>
        <div class="mb-3">
          <label>Email</label>
          <input
            type="email"
            class="form-control"
            placeholder="Masukan email Anda..."
            v-model="form.email"
          />
        </div>
        <div class="mb-3">
          <label>Pesan</label>
          <textarea
            class="form-control"
            placeholder="Masukan pesan Anda..."
            v-model="form.message"
          ></textarea>
        </div>

        <button type="submit" class="btn btn-primary">Kirim</button>
      </form>
    </div>
  </div>
</template>

<!-- Composition API -->
<script setup>
import { ref } from "vue";
const count = ref(0);
const password = ref(false);
var todos = [
  { id: 1, text: "Learn Vue 3" },
  { id: 2, text: "Learn Vue Router 4" },
  { id: 3, text: "Learn Vuex 4" },
  { id: 4, text: "Learn Pinia" },
];

var form = ref({
  name: "",
  email: "",
  message: "",
});

function showPassword() {
  password.value = !password.value;
}

const submit = e => {
  e.preventDefault();
  console.log(form.value);
};
</script>

<style>
@media (min-width: 1024px) {
  .contact {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
