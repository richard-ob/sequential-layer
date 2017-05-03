<template>
  <div class="sequential-lay-calculator">
    <div class="panel panel-info">
      <div class="panel-heading">
        <h4>Sequential Lay Calculator</h4>
      </div>
      <div class="panel-body">
        <form>
          <div class="form-group" v-for="leg in legs">
            <label>Odds</label>
            <input type="text" v-model="leg.odds"/>
            <label>Stake</label>
            <input type="text" v-model="leg.stake" disabled/>
            <button type="button" class="btn btn-danger" v-on:click="removeLeg(leg)"><i class="glyphicon glyphicon-remove"></i></button>
          </div>
        <button type="button" class="btn btn-info" v-on:click="addLeg"><i class="glyphicon glyphicon-plus"></i> Add Leg</button>
        <button type="button" class="btn btn-success" v-on:click="calculate"><i class="glyphicon glyphicon-refresh"></i> Calculate</button>
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
