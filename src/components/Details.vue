<template>
  <div v-if="machine" class="machine">
    <p class="bold">Type:</p>
    <p>{{ machine.type }}</p>
    <p class="bold">Location:</p>
    <p class="machine__coordinates">
      {{ machine.location.N }}<br />{{ machine.location.E }}<br />
      {{ machine.location.H }}
    </p>
  </div>
  <div v-else class="no-selection">no selection</div>
</template>

<script>
export default {
  props: ['machine'],
}
</script>

<style scoped>
.bold {
  font-weight: 700;
}
p {
  text-align: left;
  margin: 5px;
}
.machine {
  line-height: 1.4;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  margin: 20px 0;
}
.machine__location {
  display: flex;
}
.machine__coordinates {
  text-align: start;
}
.no-selection {
  margin: 30px;
}
</style>