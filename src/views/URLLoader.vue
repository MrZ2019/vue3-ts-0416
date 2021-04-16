<template>
  <div class="about">
    <img :src="result[0] && result[0].url" alt="" @click='getCat'>
  </div>
</template>

<script lang="ts">
  import { Vue } from 'vue-class-component';
  import { watch } from 'vue'
  import useURLLoader from '../components/useURLLoader.vue'


  interface CatResult {
    id: string;
    url: string;
    width: number;
    height: number;
  }

  export default class MouseTrack extends Vue {

    result:Array = [];

    getCat():void {
      let r = useURLLoader<CatResult[]>('https://api.thecatapi.com/v1/images/search?limit=1').result
      watch(r, () => {

        this.result = r.value
      })
    }

    created()  {
      // let result2 = ref<CatResult | null>(null);
      this.getCat()
    }

  }
</script>
