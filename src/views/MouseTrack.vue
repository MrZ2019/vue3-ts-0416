<template>
  <div class="about">
    <h1>x: {{x2}}</h1>
  </div>
</template>

<script lang="ts">
  import { Options, Vue } from 'vue-class-component';
  import Tracker from '../components/Tracker.vue'



  @Options({
    components: {
    },
  })
  export default class MouseTrack extends Vue {
    x:any
    get x2():string {
      return this.x?.value;
    }

    created()  {
      let {x, y} = Tracker()
      this.x = x
    }

  }
</script>
