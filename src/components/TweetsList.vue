<template>
  <select v-model="sortBy">
    <option value="date">Сортировать по дате</option>
    <option value="likes">Сортировать по лайкам</option>
  </select>
  <ul>
    <TweetItem v-for="item in sortedItems" :key="item.id" :item="item" />
  </ul>
</template>

<script>
  import { ref, toRefs, computed } from 'vue';
  import TweetItem from '@/components/TweetItem';
  export default {
    components: { TweetItem },
    props: {
      items: {
        type: Array,
        required: true,
      },
    },
    setup(props) {
      const { items } = toRefs(props);

      const sortBy = ref('date');
      const sortedItems = computed(() => {
        const copy = items.value;

        copy.sort((a, b) => {
          if (a[sortBy.value] > b[sortBy.value]) {
            return -1;
          }
          if (a[sortBy.value] < b[sortBy.value]) {
            return 1;
          }
        });
        return copy;
      });

      return {
        sortBy,
        sortedItems,
      };
    },
  };
</script>
