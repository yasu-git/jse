<template>
  <div>
    <ul v-if="items && items.length">
      <li v-for="item in items" :key="item.id">
        <a :href="item.url" target="_blank">{{ item.title }}</a>
        <span> - Likes: {{ item.likes_count }}</span>
      </li>
    </ul>
    <p v-else>{{ message }}</p>
  </div>
</template>

<script>
export default {
  props: {
    items: {
      type: Array,
      default: () => [],
    },
    message: {
      type: String,
      default: '',
    },
  },
};
</script>
