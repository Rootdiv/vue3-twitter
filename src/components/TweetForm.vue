<template>
  <form @submit.prevent="onSubmit">
    <textarea v-model="body" required placeholder="Введите Tweet здесь" />
    <br />
    <button class="btn btnTweet" type="submit">Отправить твит</button>
  </form>
</template>

<script>
  export default {
    data() {
      return {
        body: '',
      };
    },
    methods: {
      onSubmit() {
        this.$emit('onSubmit', {
          id: Math.round(Math.random() * 30),
          avatar: `https://avatars.dicebear.com/api/male/${Date.now()}.svg`,
          body: this.body,
          likes: 0,
          date: new Date(Date.now()).toLocaleDateString(),
        });
        this.body = '';
      },
    },
  };
</script>
