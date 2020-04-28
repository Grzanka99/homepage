<template>
  <div class="app">
    <Time />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import Time from '@/components/Time.vue';

@Component({ name: 'Home', components: { Time } })
export default class HomeComponent extends Vue {}
</script>
