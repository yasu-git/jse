<template>
  <div>
    <input
      type="text"
      v-model="keyword"
      @input="onKeywordChange"
      placeholder="Enter keyword"
    />
  </div>
</template>

<script>
export default {
  data() {
    return {
      keyword: '',
    };
  },
  methods: {
    onKeywordChange() {
      this.$emit('keyword-changed', this.keyword);
    },
  },
};
</script>
