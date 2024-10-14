<template>
  <v-card>
    <v-card-title>דירוג אמון אפס</v-card-title>
    <v-card-text>
      <div class="score">
        <h2>{{ score }}</h2>
        <span>{{ riskCategory }}</span>
      </div>
      <v-list two-line subheader>
        <v-list-item v-for="(metric, key) in metrics" :key="key">
          <v-list-item-content>
            <v-list-item-title>{{ key }}</v-list-item-title>
            <v-list-item-subtitle>{{ metric.score }}</v-list-item-subtitle>
            <v-spacer></v-spacer>
            <v-progress-linear :value="metric.score" :max="100"></v-progress-linear>
          </v-list-item-content>
          <v-list-item-description v-if="metric.description">
            {{ metric.description }}
          </v-list-item-description>
        </v-list-item>
      </v-list>
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  props: {
    score: Number,
    metrics: Object,
    riskCategory: String,
  },
};
</script>

<style scoped>
.score {
  display: flex;
  align-items: center;
  justify-content: space-between;
  font-size: 2em;
  margin-bottom: 1em;
}
</style>