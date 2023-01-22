<template>
  <div class="alert alert-primary">
    <h3>Success: {{ stats.success }}</h3>
    <h3>Error: {{ stats.error }}</h3>
    <hr />
    <button class="btn btn-primary mx-2" @click="$emit('repeat')">
      Repeat
    </button>
    <button
      class="btn btn-primary"
      v-if="!isLastLevel"
      @click="$emit('nextLevel')"
    >
      Next Level
    </button>
    <button v-else class="btn btn-success mx-2" @click="$emit('restart')">
      Restart
    </button>
  </div>
</template>

<script>
export default {
  props: ["stats", "questMax", "level"],
  computed: {
    isLastLevel() {
      const actualLevel = this.level + 1;
      return actualLevel >= this.questMax;
    },
  },
};
</script>

<style>
</style>