<template>
  <div id="app">
    <div class="jumbotron jumbotron-fluid text-center">
      <div class="container">
        <div class="row">
          <div class="col">
            <h1 class="display-4">Workout Maker</h1>
            <button @click="random" class="btn btn-primary">
              Make Combined Workout
            </button>
            <div class="my-4">
              <span
                v-for="movement in sample"
                :key="movement"
                class="mx-1 badge badge-dark"
              >
                {{ movement }}
              </span>
            </div>
            <div v-if="isSwole" class="alert alert-success">IS SWOLE.</div>
          </div>
        </div>
      </div>
    </div>

    <div class="container">
      <div class="row">
        <div class="col">
          <h2 class="display-6 text-center">Upper</h2>
          <ul class="list-group">
            <li v-for="top in upper" :key="top" class="list-group-item">
              {{ top }}
            </li>
          </ul>
        </div>
        <div class="col">
          <h2 class="display-6 text-center">Lower</h2>
          <ul class="list-group">
            <li v-for="bottom in lower" :key="bottom" class="list-group-item">
              {{ bottom }}
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { sampleSize } from 'lodash';

export default {
  name: 'app',
  data() {
    return {
      upper: [
        'bench press',
        'curls',
        'push ups',
        'overhead press',
        'pull ups',
        'shoulder raise',
      ],
      lower: [
        'squats',
        'bulgarian split squats',
        'deadlifts',
        'ham curls',
        'calf raises',
        'box jumps',
      ],
      sample: [],
    };
  },
  methods: {
    random() {
      this.sample = [
        ...sampleSize(this.upper, 3),
        ...sampleSize(this.lower, 3),
      ];
    },
  },
  computed: {
    isSwole() {
      return this.sample.includes('deadlifts');
    },
  },
};
</script>

<style></style>
