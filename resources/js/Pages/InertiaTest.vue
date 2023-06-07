<script setup>
  import { Link } from '@inertiajs/vue3';
  import { ref } from 'vue'

  const newTitle = ref('')
  const newContent = ref('')

</script>



<template>
Inertiaテストです<br>
<a href="/">aタグ経由です</a><br>
<Link href="/">Linkタグ経由です</Link><br>
<Link :href="route('inertia.index')">名前つきルートの確認です</Link><br>
<Link :href="route('inertia.show', { id: 50 })">ルートパラメーターのテストです</Link>

<div class="mb-8"></div>
<input type="text" name="newTitle" v-model="newTitle">{{ newTitle }}<br>
<input type="text" name="newContent" v-model="newContent">{{ newContent }}<br>
<Link as="button" method="post" :href="route('inertia.store')"
:data="{
  title: newTitle,
  content: newContent
}">DB保存つと</Link>

</template>