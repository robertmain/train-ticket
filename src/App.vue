<template>
  <div id="app">
    <ticket></ticket>
  </div>
</template>

<script>
import Ticket from './components/Ticket';

export default {
  name: 'app',
  components: {
    Ticket
  }
}
</script>

<style lang="scss">
@import "reset-css";
@import url(https://fonts.googleapis.com/css?family=Old+Standard+TT|Jura|Questrial|Inconsolata|Montserrat);

</style>
