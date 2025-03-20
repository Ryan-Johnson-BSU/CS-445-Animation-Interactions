<script>

import Card from 'primevue/card';
import { ref } from 'vue'

const show = ref ( true )

export default {
  components: {
    Card
  },
  setup() {
    const cards = ref([
      {front: 'Front', back: 'Back'},
      {front: 'Hello', back: 'Goodbye'},
      {front: 'Left', back: 'Right'},
      {front: 'Up', back: 'Down'},
      {front: 'Standing', back: 'Sitting'},
      {front: 'Running', back: 'Walking'},
      {front: 'Open', back: 'Closed'},
      {front: 'On', back: 'Off'}
    ]);

    return {
      cards
    };
  }
}
</script>

<template>
    <div class = "flip-box"
    v-for = "(card, index) in cards"
    :key = "index">
    <div class="flip-box-inner">
      <Card class="flip-box-front">
        <template #title>{{card.front}}</template>
      </Card>
      <Card class="flip-box-back">
        <template #title>{{card.back}}</template>
      </Card>
      </div>
    </div>


</template>


  
<style scoped>


.flip-box {
  background-color: transparent;
  width: 300px;
  height: 200px;

  perspective: 1000px; /* Remove this if you don't want the 3D effect */
}

/* This container is needed to position the front and back side */
.flip-box-inner {
  position: relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 0.8s;
  transform-style: preserve-3d;
}

/* Do an horizontal flip when you move the mouse over the flip box container */
.flip-box:hover .flip-box-inner {
  transform: rotateY(180deg);
}

/* Position the front and back side */
.flip-box-front, .flip-box-back {
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden; /* Safari */
  backface-visibility: hidden;
}

/* Style the front side */
.flip-box-front {
  background-color: dodgerblue;
  color: white;
}

/* Style the back side */
.flip-box-back {
  background-color: rgb(15, 63, 112);
  color: white;
  transform: rotateY(180deg);
}

</style> 
