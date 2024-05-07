<script>
import { store } from "../store";
export default {
  data() {
    return {
      store,
      archetipes: ["All", "Archfiend", "Alien", "Noble Knight"],
    };
  },
};
</script>

<template>
  <div class="container py-4">
    <div class="d-flex justify-content-between">
      <div>
        <select @change="$emit('filter')" v-model="store.selectedArchetype">
          <option :value="archetipe" v-for="archetipe in archetipes">
            {{ archetipe }}
          </option>
        </select>
      </div>

      <p>Mostrati {{ store.cardsList.length }} elementi</p>
    </div>
  </div>
</template>
