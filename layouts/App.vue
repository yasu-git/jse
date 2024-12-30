<template>
  <div>
    <h1>Search App</h1>
    <SearchBox @keyword-changed="getAnswer" />
    <ResultsList :items="items" :message="message" />
  </div>
</template>

<script>
import SearchBox from './components/SearchBox.vue';
import ResultsList from './components/ResultsList.vue';
import axios from 'axios';

export default {
  components: {
    SearchBox,
    ResultsList,
  },
  data() {
    return {
      items: null,
      message: '',
    };
  },
  methods: {
    getAnswer(keyword) {
      if (!keyword.trim()) {
        this.items = null;
        this.message = '';
        return;
      }
      this.message = 'Loading...';
      axios
        .get('https://qiita.com/api/v2/items', {
          params: { query: keyword, page: 1, per_page: 20 },
        })
        .then((response) => {
          this.items = response.data;
          this.message = '';
        })
        .catch((error) => {
          this.items = null;
          this.message = `Error: ${error.message}`;
        });
    },
  },
};
</script>
