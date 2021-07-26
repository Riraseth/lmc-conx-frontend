<template>
  <div class="fleet-manager">
    <div class="list"><Machines @machineDetails="machineDetails" /></div>
    <div class="details border"><Details :machine="machine" /></div>
  </div>
</template>

<script>
import Machines from './Machines.vue'
import Details from './Details.vue'
export default {
  name: 'FleetManager',
  components: {
    Machines,
    Details,
  },
  data() {
    return {
      machine: '',
    }
  },
  methods: {
    machineDetails(machine) {
      this.machine = machine
      console.log(this.machine)
    },
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.fleet-manager {
  max-width: 600px;
  margin: 0 auto;
  display: grid;
  gap: 20px;
  grid-template-columns: 1fr 2fr;
  padding: 20px;
}

.details {
  display: flex;
  align-items: center;
  justify-content: center;
}
ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

@media screen and (max-width: 530px) {
  .fleet-manager {
    display: block;
  }
  .list {
    margin-bottom: 12px;
  }
}
</style>
