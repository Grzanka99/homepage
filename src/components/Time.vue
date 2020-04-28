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
import { Days, Months } from '@/assets/types/enums';

interface Time {
  date: string;
  hours: number;
  minutes: number;
}

export default {
  name: 'Time',
  data() {
    return {
      time: {
        date: '',
        hours: 0,
        minutes: 0,
      },
    };
  },
  methods: {
    getTime(): Time {
      const d = new Date();

      return {
        date: `${Days[d.getDay()]}, ${d.getDate()} ${Months[d.getMonth()]} ${d.getFullYear()}`,
        hours: d.getHours(),
        minutes: d.getMinutes(),
      };
    },
  },
  created() {
    this.time = this.getTime();

    setInterval((): void => {
      this.time = this.getTime();
    }, 5000);
  },
};
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
