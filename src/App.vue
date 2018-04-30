<template>
  <div id='app'>
    <h1>{{currentDate}}</h1>
    <h1>{{ relizeDate }}</h1>
    <p>
      <ul>
        <li>{{ relizeDate.getMonth() - currentDate.getMonth() }}</li>
        <li>relizeDays : {{ (Math.floor(Math.round(relizeDate-currentDate)/86400000) < 1) ? "0"+Math.floor(Math.round(relizeDate-currentDate)/86400000) : Math.floor(Math.round(relizeDate-currentDate)/86400000) }}</li>
        <li> relizeHour: {{ ((24 - currentDate.getHours() - 1 ) < 10) ? "0"+(24 - currentDate.getHours() - 1) : 24 - currentDate.getHours() - 1 }}</li>
        <li> relizeMins: {{ ((60 - currentDate.getMinutes() - 1) < 10) ? "0"+(60 - currentDate.getMinutes() - 1) : 60 - currentDate.getMinutes() - 1 }}</li>
        <li> relizeSeconds: {{ ((60 - currentDate.getSeconds() - 1) < 10) ? "0"+(60 - currentDate.getSeconds() - 1) : (60 - currentDate.getSeconds() - 1) }}</li>
        <li>{{ -1*(relizeDate.getSeconds() - currentDate.getSeconds()) }}</li>
      </ul>
    </p>
  </div>
</template>

<script>
import Times from './Times.vue'
export default {
  components: {
    Times
  },
  data: function() {
    return {
      currentDate: new Date(),
      relizeDate: new Date('2018-08-30 00:00'),
      relizeHour: 0
    }
  },
  watch: {
    currentDate: function(){
      this.relizeHour = ((24 - this.currentDate.getHours() - 1 )< 10) ? "0"+(24 - this.currentDate.getHours() - 1) : 24 - this.currentDate.getHours() - 1
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
