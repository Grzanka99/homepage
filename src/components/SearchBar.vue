<template>
  <div class="searchbar">
    <label for="find" class="searchbar__label" v-show="!find">Search something</label>
    <input type="text" name="find" id="find" v-model="find" class="searchbar__input" />
    <button class="searchbar__button"></button>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Watch } from 'vue-property-decorator';

@Component({ name: 'SearchBar' })
export default class SearchBarComponent extends Vue {
  find = '';

  @Watch('find')
  onFindChange() {
    return 0;
  }
}
</script>

<style lang="scss" scoped>
@import '@/assets/scss/vars.scss';

$box-shadow-inset: 0 -5px 0 rgba(black, 0.25) inset;

.searchbar {
  position: absolute;
  align-self: center;
  left: calc(50% - 400px);

  width: 800px;
  height: 100px;
  overflow: hidden;

  display: flex;
  justify-content: center;
  align-items: center;

  border-radius: 50px;
  box-shadow: 0 4px 4px rgba(black, 0.25);

  font-family: 'Fira Sans';

  &__input {
    position: relative;
    display: flex;

    width: 650px;
    height: 100px;
    border-radius: 50px 0 0 50px;

    font-size: 40px;
    padding: 0 0 0 25px;

    background-color: $nord5;
    box-shadow: $box-shadow-inset;
    border: none;

    text-align: center;
    color: rgba($nord0, 0.7);
    font-family: 'Fira Sans';
    font-weight: 400;
  }

  &__button {
    position: relative;

    width: 150px;
    height: 100px;
    border-radius: 0 50px 50px 0;

    background-image: url('../assets/find.svg');
    background-position: center;
    background-repeat: no-repeat;
    background-size: 70px;

    background-color: $nord3;
    box-shadow: $box-shadow-inset;
    border: none;
    z-index: 1;

    &::before {
      content: '';
      display: block;
      width: 5px;
      height: 95px;

      position: absolute;
      top: 0;
      left: -5px;

      background-color: $nord4;
    }
  }

  &__label {
    position: absolute;

    color: rgba($nord0, 0.5);
    font-size: 40px;
    font-weight: 700;

    transform: translate(-75px, 0);

    z-index: 1;
  }
}
</style>
