<template>
  <div class="flex items-center justify-center min-h-screen bg-gray-100">
    <div class="px-8 py-6 mt-4 text-left bg-white shadow-lg">
      <h3 class="text-2xl font-bold text-center">Login</h3>
      <form @submit="checkForm" action="/manager">
        <div class="mt-4">
          <div>
            <label class="block" for="user">Usuario</label>
            <input type="text" placeholder="Usuario" v-model="username" class="w-full px-4 py-2 mt-2 border rounded-md focus:outline-none focus:ring-1 focus:ring-blue-600">
          </div>
          <div class="mt-4">
            <label class="block">Contraseña</label>
            <input type="password" placeholder="Contraseña"  v-model="password" class="w-full px-4 py-2 mt-2 border rounded-md focus:outline-none focus:ring-1 focus:ring-blue-600">
          </div>
          <div class="flex items-baseline justify-between">
              <button type="submit" class="px-6 py-2 mt-4 text-white bg-blue-600 rounded-lg hover:bg-blue-900">Login</button>
          </div>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  data() {
    return {
      username: "",
      password: ""
    }
  },
  methods: {
    checkForm(e){
      if(this.username !== "" && this.password !== ""){

        if(this.username == "test01" && this.password == "test01"){
          return true;
        }        
      }

      e.preventDefault();
    }
  }
}
</script>
