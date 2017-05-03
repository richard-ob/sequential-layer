<template>
  <div class="sequential-lay-calculator">
    <div class="panel panel-default">
      <div class="panel-heading">
        <h4>Sequential Lay Calculator</h4>
      </div>
      <div class="panel-body">
        <form>
          <div class="alert alert-info">
            <h4>Back Bet</h4>
            <div class="form-group">
              <label>Odds</label>
              <input type="text" v-model="backBet.odds"/>
              <label>Stake</label>
              <input type="text" v-model="backBet.stake"/>
            </div>
          </div>
          <div class="alert alert-danger">
            <h4>Lay Bets</h4>
            <div class="form-group" v-for="leg in legs">
              <label>Odds</label>
              <input type="text" v-model="leg.odds"/>
              <label>Stake</label>
              <input type="text" v-model="leg.stake" disabled/>
              <button type="button" class="btn btn-danger" v-on:click="removeLeg(leg)"><i class="glyphicon glyphicon-remove"></i></button>
            </div>
            <button type="button" class="btn btn-default" v-on:click="addLeg"><i class="glyphicon glyphicon-plus"></i> Add Leg</button>
          </div>
          <div class="text-center">
            <button type="button" class="btn btn-success" v-on:click="calculate"><i class="glyphicon glyphicon-refresh"></i> Calculate</button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'sequential-lay-calculator',
  data () {
    return {
      backBet: {odds: 1.5, stake: 25},
      legs: [
        {odds: 1.5, stake: 0},
        {odds: 1.5, stake: 0},
        {odds: 2, stake: 0}
      ]
    }
  },
  methods: {
    addLeg: function () {
      this.legs.push({odds: 1.5, stake: 0})
    },
    removeLeg: function (leg) {
      this.legs = this.legs.filter(l => l !== leg)
    },
    calculate: function () {
      this.legs[0].odds = 9
    }
  }
}
</script>

<style scoped>
  .sequential-lay-calculator {
    padding-top: 65px;
  }
</style>
