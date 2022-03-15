<!-- Please remove this file from your project -->
<template>
<div class="w-full h-screen">
    <div class="h-96"></div>
    <div class="max-w-5xl mx-auto px-6 sm:px-6 lg:px-8 mb-12">
        <div class="w-full shadow rounded p-8 sm:p-12 -mt-72 ">
              <div class="mt-12 mb-5 w-full text-center relative relative flex flex-wrap justify-center">
              <h1 class=" nuestrosAticles z-10 my-6 text-3xl">Contáctanos</h1>
              <img class="brushArticle absolute z-0" src="/BRUSH.png" alt="BRUSH">
              <div class="md:flex  space-y-3 md:space-y-0 md:space-x-4 mt-6"></div>
          </div>
                <div class="md:flex items-center mt-12">
                    <div class="w-full md:w-1/2 flex flex-col">
                        <label class="font-semibold leading-none uppercase">nombre</label>
                        <input v-model="info.firstname" type="text" class="leading-none p-3 focus:outline-none focus:border-yellow-700 mt-4 border  rounded" />
                    </div>
                    <div class="w-full md:w-1/2 flex flex-col md:ml-6 md:mt-0 mt-4">
                        <label class="font-semibold leading-none uppercase">apellido</label>
                        <input v-model="info.lastname" type="email" class="leading-none p-3 focus:outline-none focus:border-yellow-700 mt-4 border rounded"/>
                    </div>
                </div>
                <div class="md:flex items-center mt-8">
                  <div class="w-full md:w-1/2 flex flex-col">
                        <label class="font-semibold leading-none uppercase">mail</label>
                        <input v-model="info.email" type="text" class="leading-none p-3 focus:outline-none focus:border-yellow-700 mt-4 border  rounded" />
                    </div>
                    <div class="w-full md:w-1/2 flex flex-col md:ml-6 md:mt-0 mt-4">
                        <label class="font-semibold leading-none uppercase">teléfono</label>
                        <input v-model="info.phone" type="email" class="leading-none p-3 focus:outline-none focus:border-yellow-700 mt-4 border rounded"/>
                    </div>
                </div>
                <div class="flex items-center justify-end w-full">
                    <button @click="submit()" class="mt-9 flex font-semibold leading-none text-white uppercase py-4 px-10 bg-yellow-700 rounded hover:bg-yellow-600 focus:ring-2 focus:ring-offset-2 focus:ring-blue-700 focus:outline-none">
                        <img v-if="loading" src="/Spinner-1s-200px.svg" alt="loading" class="h-5 h-5">
                        Enviar
                    </button>
                    
                </div>
        </div>
    </div>
</div>
</template>

<script>

import axios from 'axios'
export default {
  name: 'Contact',
  data: () => ({
    loading: false,
    info:{
      firstname: '',
      lastname: '',
      email: '',
      phone: ''
    }
  }),
  methods: {
    async submit() {
      try {
        this.loading = true
        await axios.post('https://5eed24da4cbc340016330f0d.mockapi.io/api/newsletter', this.info)
      } catch (error) {
        console.log(error)
      }finally{
        this.loading = false
        this.info = {
          firstname: '',
          lastname: '',
          email: '',
          phone: ''
        }
      }
    }
  }
}
</script>

<style>
.nuestrosAticles{
  z-index: 10;
  font-family: 'Caveat', cursive;
  font-size: 80px;
  font-weight: 700;
  color: #3F3356;

  @media (max-width: 768px) {
    font-size: 50px;
  }

  @media (max-width: 576px) {
    font-size: 30px;
  }

  @media (max-width: 480px) {
    font-size: 20px;
  }
}
.brushArticle{
  z-index: 0;
  margin-top: 50px;
  margin-right: -50px;
  height: 70px;
  width: 500px;
  opacity: 0.2;
}
.categori{
  font-family: 'Open Sans', sans-serif;
  font-size: 12px;
  line-height: 23px;
  /* or 192% */

  letter-spacing: 0.03em;
  text-transform: uppercase;
}
</style>
