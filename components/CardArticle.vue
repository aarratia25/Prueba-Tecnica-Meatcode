<!-- Please remove this file from your project -->
<template>
<div class="shadow-lg rounded-md overflow-hidden">
  <div class="">
    <img class="w-sm" :src="article.image" alt="" />
    <div class="p-2 relative pb-12">
          <p class="text-lg mt-6 font-semibold">{{article.title}}</p>
          <p>{{article.content}}</p>
    </div>
  </div>
</div>
</template>

<script>
export default {
  name: 'CardArticle',
  props: {
    article: {
      type: Object
    }
  },
}
</script>
