<template>

<div v-if="nama == ''" class="fixed top-0 left-0 w-screen h-screen bg-[#00000091] z-20 flex justify-center items-center">
  <div class="bg-white w-[94vw] px-3 py-5 rounded-lg">
    <p class="font-pupylinux text-center mb-5">Selamat Datang Di Todo App Gwej</p>

    <form @submit.prevent="addname">
    <input type="text" placeholder="Nama luwh siafkh" required name="nama" class="border-b-2 border-yellow-300 p-2 w-[290px]">
    <button class="bg-yellow-300 py-2 px-4 ml-3 rounded-full font-pupylinux" type="submit">Save</button>
    </form>

  </div>
</div>

  <p class="ml-[45px] mt-6 text-2xl pr-4 font-medium font-pupylinux dark:text-white">{{ waktu }} {{ nama }}</p>
  <Todo />

  
</template>

<script>
import Todo from "../components/Todo.vue";
export default {
  data() {
    return {
      nama: '',
      waktu: ''
    }
  },
  created() {
    if (localStorage.nama) {
      this.nama = localStorage.getItem('nama')
    }
  },
  methods: {
    addname(e){
      localStorage.setItem('nama', e.target.nama.value)
      this.nama = e.target.nama.value
    }
  },
  mounted() {
    const date = new Date
    if (date.getHours() < 3 ) {
      this.waktu = 'Jangan Lupa Tidur Ya'
    }else if (date.getHours() < 10) {
      this.waktu = 'Selamat Oagi'
    }else if (date.getHours() < 13){
      this.waktu = 'Selamat Siang'
    }else if (date.getHours() < 18){
      this.waktu = 'Selamat Sore'
    }else{
      this.waktu = 'Selamat Malam'
    }
  },
    components: { Todo }
}
</script>
