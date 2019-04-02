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
          </div>
        </div>
      </div>
    </div>

    <div class="container">
      <div class="row">
        <div class="col">
          <h1>Upper</h1>
          <ul>
            <li v-for="top in upper" :key="top">
              {{ top }}
            </li>
          </ul>
        </div>
        <div class="col">
          <h1>Lower</h1>
          <ul>
            <li v-for="bottom in lower" :key="bottom">
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
};
</script>

<style></style>
