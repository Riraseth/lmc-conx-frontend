<template>
  <div
    v-for="machine in activeMachines"
    :key="machine.id"
    @click="selectMachine(machine)"
    class="machine border"
    :class="{ active: machine.id === selectedMachineId }"
  >
    <span>
      {{ machine.make }}
    </span>
  </div>
</template>

<script>
import machines from '../api/mockApi'
export default {
  emits: ['machineDetails'],
  data() {
    return {
      machines: machines,
      selectedMachineId: '',
      selectedMachine: '',
    }
  },
  computed: {
    activeMachines() {
      return this.machines.filter((machine) => machine.active)
    },
  },
  methods: {
    selectMachine(machine) {
      if (this.selectedMachineId === machine.id) {
        this.selectedMachineId = ''
        this.selectedMachine = ''
      } else {
        this.selectedMachineId = machine.id
        this.selectedMachine = machine
      }
      this.$emit('machineDetails', this.selectedMachine)
    },
  },
}
</script>

<style scoped>
.machine {
  padding: 10px 15px;
  cursor: pointer;
}
.machine:not(:last-child) {
  margin-bottom: 8px;
}
.machine.active {
  background-color: #1e1e1e;
}
.machine.active span {
  color: #fff;
}
</style>