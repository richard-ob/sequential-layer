<template>
  <div class="sequential-lay-calculator">
    <div class="panel panel-default">
      <div class="panel-heading">
        <h4><i class="fa fa-calculator text-muted"></i> Sequential Lay Calculator</h4>
      </div>
      <div class="panel-body">
        <form>
          <div class="alert alert-info">
            <h4>Back Bet</h4>
            <div class="row">
              <div class="col-sm-5">
                <div class="form-group">
                  <label>Odds</label>
                  <input type="text" v-model="backBet.odds" class="form-control"/>
                </div>            
              </div>
              <div class="col-sm-5">
                <div class="form-group">
                  <label>Stake</label>
                  <input type="text" v-model="backBet.stake" class="form-control"/>
                </div>
              </div>
            </div>
          </div>
          <div class="alert alert-danger">
            <h4>Lay Bets</h4>
            <div class="row" v-for="leg in legs" v-bind:key="leg.id">
              <div class="col-sm-5">
                <div class="form-group">
                  <label>Odds</label>
                  <input type="text" v-model="leg.odds" class="form-control"/>
                </div>
              </div>
              <div class="col-sm-5">
                <div class="form-group">
                  <label>Stake</label>
                  <input type="text" v-model="leg.stake" class="form-control" disabled/>
                </div>
              </div>
              <div class="col-sm-2">
                <button type="button" style="margin-top: 25px;" class="btn btn-danger" v-on:click="removeLeg(leg)">
                  <i class="glyphicon glyphicon-remove"></i>&nbsp;Remove
                </button>
              </div>
            </div>
            <button type="button" class="btn btn-primary" v-on:click="addLeg">
              <i class="glyphicon glyphicon-plus"></i>&nbsp;Add Leg
            </button>
          </div>
          <div class="text-center">
            <button type="button" class="btn btn-success" v-on:click="calculate">
              <i class="glyphicon glyphicon-refresh"></i>&nbsp;Calculate
            </button>
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
      this.legs.push({odds: 1.5, stake: 0, id: this.legs.length})
    },
    removeLeg: function (leg) {
      this.legs = this.legs.filter(l => l !== leg)
    },
    calculate: function () {
    }
  }
}
</script>

<style scoped>
  .sequential-lay-calculator {
    padding-top: 65px;
  }
</style>
