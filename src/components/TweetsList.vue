<template>
  <ul>
    <TweetItem v-for="item in items" :key="item.id" :item="item" />
  </ul>
</template>

<script>
  import TweetItem from '@/components/TweetItem';
  export default {
    components: { TweetItem },
    props: {
      items: {
        type: Array,
        required: true,
      },
    },
  };
</script>
