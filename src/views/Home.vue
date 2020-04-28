<template>
  <div class="app">
    <Time />
    <SearchBar />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

import Time from '@/components/Time.vue';
import SearchBar from '@/components/SearchBar.vue';

@Component({ name: 'Home', components: { Time, SearchBar } })
export default class HomeComponent extends Vue {}
</script>

<style lang="scss" scoped>
.app {
  width: 100%;
  height: 100vh;

  display: flex;
}
</style>
