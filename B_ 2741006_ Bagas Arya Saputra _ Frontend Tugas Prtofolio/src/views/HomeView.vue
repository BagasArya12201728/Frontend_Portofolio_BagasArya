<script>
import BaseCard from '@/components/Base/CardComp.vue';

import imageStore from '@/stores/image';

import { mapState } from 'pinia';

export default {
  name: 'HomePage',
  components: {
    BaseCard,
  },
  computed: {
    ...mapState(imageStore, ['g$list']),
  }
};
</script>

<template>
  <section style="text-align: center; font-family:'Times New Roman', Times, serif">
    <h2>My Project</h2>

    <div class="grid-container">
      <template v-for="(img, index) in g$list" :key="index">
        <RouterLink :to="{ name:'detail',params: { id: img.slug }}">
        <BaseCard :data="img"/>
        </RouterLink>
      </template>
    </div>
  </section>
</template>

<style lang="scss">
.grid-container {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1rem;
  
}

</style>