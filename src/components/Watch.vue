<template>
  <div>
    <div class="container">
      <p class="date">{{ year }}/{{ month }}/{{ day }}</p>
      <div class="time">
        <p class="time-item hours">{{ hours }}</p>
        <p class="time-item minutes">{{ minutes }}</p>
        <p class="time-item seconds">{{ seconds }}</p>
      </div>
    </div>
  </div>
</template>

<script>
const zeroPadding = (num, length) => {
  return (Array(length).join('0') + num).slice(-length);
};

export default {
  name: 'Watch',
  data() {
    return {
      date: new Date()
    };
  },
  computed: {
    year() {
      return this.date.getFullYear();
    },
    month() {
      return zeroPadding(this.date.getMonth() + 1, 2);
    },
    day() {
      return zeroPadding(this.date.getDate(), 2);
    },
    hours() {
      return zeroPadding(this.date.getHours(), 2);
    },
    minutes() {
      return zeroPadding(this.date.getMinutes(), 2);
    },
    seconds() {
      return zeroPadding(this.date.getSeconds(), 2);
    }
  },
  mounted() {
    this.setDate();
    setInterval(() => this.setDate(), 1000);
  },
  methods: {
    setDate() {
      this.date = new Date();
    }
  }
};
</script>

<style scoped>
.container {
  padding: 2%;
  background-color: #468536;
}

.date {
  margin: 0.5em 0;
  font-family: 'Teko', sans-serif;
  font-size: 4rem;
  line-height: 1;
  color: #fff;
  text-align: center;
  letter-spacing: 0.5em;
}

.time {
  display: flex;
}

.time-item {
  position: relative;
  z-index: 1;
  box-sizing: border-box;
  display: flex;
  flex: 1 1;
  align-items: center;
  justify-content: center;
  height: 100px;
  padding: 0.5em;
  margin: 3px;
  font-family: 'Roboto Mono', monospace;
  font-size: 3rem;
  line-height: 1;
  color: #fff;
  background-color: #a23e3e;
}

.time-item::before {
  position: absolute;
  right: 5px;
  bottom: 1px;
  z-index: 1;
  font-family: 'Teko', sans-serif;
  font-size: 1.4rem;
  color: #fdfdfd;
  letter-spacing: 0.05em;
}

.hours::before {
  content: 'Hours';
}

.minutes::before {
  content: 'Minutes';
}

.seconds::before {
  content: 'Seconds';
}
</style>
