<template>
  <div class="time">
    <div class="time__clock">
      <span class="time__clock__hours">{{ time.hours }}:</span>
      <span class="time__clock__minutes">{{ time.minutes }}</span>
    </div>
    <div class="time__date">
      {{ time.date }}
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import { Days, Months } from '@/assets/types/enums';

interface Time {
  date: string;
  hours: string | number;
  minutes: string | number;
}

@Component({ name: 'Time' })
export default class TimeComponent extends Vue {
  time: Time = this.getTime();

  getTime(): Time {
    const d = new Date();
    const hours = d.getHours();
    const minutes = d.getMinutes();

    return {
      date: `${Days[d.getDay()]}, ${d.getDate()} ${Months[d.getMonth()]} ${d.getFullYear()}`,
      hours: hours > 9 ? hours : `0${hours}`,
      minutes: minutes > 9 ? minutes : `0${minutes}`,
    };
  }

  created() {
    setInterval((): void => {
      this.time = this.getTime();
    }, 1000);
  }
}
</script>

<style lang="scss" scoped>
@import '@/assets/scss/vars.scss';

.time {
  position: relative;
  top: 25px;
  left: 25px;

  width: 400px;
  height: 200px;
  border-radius: 25px;

  background-color: $nord3;
  box-shadow: 4px 4px 0 rgba(black, 0.25);

  font-family: 'Fira Code', monospace;

  &__clock {
    position: relative;
    top: 15px;
    left: 15px;

    width: 300px;
    height: 125px;
    border-radius: 25px;

    background-color: $nord4;
    box-shadow: 2px 2px 0 rgba(black, 0.25);

    display: flex;
    justify-content: center;
    align-items: center;

    font-size: 90px;

    &__hours {
      color: $nord0;
    }

    &__minutes {
      color: $nord11;
    }
  }

  &__date {
    position: relative;
    left: 20px;
    top: 30px;

    font-size: 22px;
    color: rgba($nord4, 0.5);
  }
}
</style>
