<!-- Please remove this file from your project -->
<template>
<div 
  @click="$emit('selectCategory', category.name)" 
  class="w-full flex mx-4  my-4 cursor-pointer hover:text-yellow-500  duration-150 justify-between"
  :class="{'text-yellow-500': categorySelect == category.name}">
  <span class="categori">{{category.name}}</span>
  <svg v-if="categorySelect == category.name" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 32 32" width="18" height="20"><path fill="#D8AD3D" d="m31.71 15.29-10-10-1.42 1.42 8.3 8.29H0v2h28.59l-8.29 8.29 1.41 1.41 10-10a1 1 0 0 0 0-1.41z" data-name="3-Arrow Right"/></svg>
</div>
</template>

<script>
export default {
  name: 'CardCategory',
  props: {
    category: {
      type: Object
    },
    categorySelect: {
      type: String
    }
  },
  
}
</script>

<style>
.categori{
  font-family: 'Open Sans', sans-serif;
  font-size: 12px;
  line-height: 23px;
  /* or 192% */

  letter-spacing: 0.03em;
  text-transform: uppercase;
}
</style>

