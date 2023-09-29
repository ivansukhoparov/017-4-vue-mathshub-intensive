<script setup>
import { ref } from "vue";

let counter = ref(0);

let dwarves = ref([
  {
    name: "Thorin",
    age: 195,
    leader: true
  },
  {
    name: "Balin",
    age: 178,
    leader: false
  },
  {
    name: "Fili",
    age: 82,
    leader: false
  },
  {
    name: "Kili",
    age: 79,
    leader: false
  },
]
);

function handleClick(dwarf) {
  dwarves.value.forEach((el) => { el.leader = false });
  dwarf.leader = true;
};


</script>

<template>
  <ul>
    <li v-for="dwarf in      dwarves     " :key="dwarf.name" @click="() => handleClick(dwarf)"
      :class="{ marked: dwarf.leader }">
      <span v-if="dwarf.age > 100">Old </span>
      <span v-else>Young </span>
      <span>{{ dwarf.name }} is {{ dwarf.age }} y.o. {{ dwarf.leader }}</span>
    </li>

  </ul>
</template>
<style scoped>
.marked {
  color: red;
}
</style>
