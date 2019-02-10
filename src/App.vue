<template>
  <div id="app">
    <form>
      <label for="passenger">Passenger</label><input name="passenger" type="text" v-model="newTicket.passenger"><br />
      <br />
      <label for="passenger">Departs From:</label><input name="depart" type="text" v-model="newTicket.depart"><br />
      <br />
      <label for="arrive">Departs At:</label><input name="arrive" type="datetime-local" v-model="newTicket.departs"><br />
      <br />
      <label for="arrive">Arrives At:</label><input name="arrive" type="text" v-model="newTicket.arrive"><br />
      <br />
      <button type="button" @click="createTicket(newTicket)">Create New Ticket</button>
    </form>
    <div class="tickets">
      <ticket v-for="ticket in tickets" :key="ticket.id"
        :id="ticket.id"
        :passenger="ticket.passenger"
        :departs="ticket.departs"
        :depart="ticket.depart"
        :arrive="ticket.arrive"
        :car="ticket.car"
        :seat="ticket.seat"
      ></ticket>
      <p v-if="tickets.length == 0">
        <em>There are no tickets available for display</em>
      </p>
    </div>
  </div>
</template>

<script>
import Ticket from './components/Ticket';

export default {
  name: 'app',
  data() {
    return {
      newTicket: {
        passenger: '',
        departs: '',
        depart: '',
        arrive: '',
        seat: '',
        car: '',
      },
      tickets: [],
    }
  },
  methods: {
    createTicket(ticket) {
      this.tickets.push({
        ...ticket,
        id: Math.floor(Math.random() * 999999999) + 1,
      });
      this.clearNewTicket();
    },
    clearNewTicket() {
      this.newTicket = {
        passenger: '',
        departs: '',
        depart: '',
        arrive: '',
      };
    }
  },
  components: {
    Ticket
  }
}
</script>

<style lang="scss">
@import "reset-css";
@import url(https://fonts.googleapis.com/css?family=Old+Standard+TT|Jura|Questrial|Inconsolata|Montserrat);

$spacing-hairline: 1px;
$spacing-small: 5px;
$spacing-medium: 10px;
$spacing-large: 20px;
$spacing-xlarge: 40px;
$spacing-xxlarge: 80px;

#app{
  max-width: 1600px;
  margin: $spacing-xxlarge auto;
}

.tickets {
  display: block;
  margin-top: $spacing-xxlarge;
  border-top: 1px solid #AAAA;
  overflow: hidden;
  padding: $spacing-large 0px;
  height: 700px;
  overflow-y: auto;
}

.ticket{
  cursor: pointer;
  float: left;
  margin: 0px $spacing-xlarge $spacing-xlarge 0px;
}

form{
  display: inline-block;
  background-color: white;
  padding: $spacing-large;
  border: 1px solid lightgrey;

  input{
    border: 1px solid lightgrey;
  }
}
</style>
