<template>
  <form @submit.prevent="onSubmit">
    <textarea v-model="body" required placeholder="Введите Tweet здесь" />
    <br />
    <button class="btn btnTweet" type="submit">Отправить твит</button>
  </form>
</template>

<script>
  import { ref } from 'vue';
  export default {
    emits: ['onSubmit'],
    //При деструктуризации context необходимо указать props или знак подчёркивания
    setup(_, { emit }) {
      const body = ref('');
      const onSubmit = () => {
        emit('onSubmit', {
          id: Math.round(Math.random() * 30),
          avatar: `https://avatars.dicebear.com/api/male/${Date.now()}.svg`,
          body: body.value,
          likes: 0,
          date: new Date(Date.now()).toLocaleString(),
        });
        body.value = '';
      };
      return {
        body,
        onSubmit,
      };
    },
    // data() {
    //   return {
    //     body: '',
    //   };
    // },
    // methods: {
    //   onSubmit() {
    //     this.$emit('onSubmit', {
    //       id: Math.round(Math.random() * 30),
    //       avatar: `https://avatars.dicebear.com/api/male/${Date.now()}.svg`,
    //       body: this.body,
    //       likes: 0,
    //       date: new Date(Date.now()).toLocaleString(),
    //     });
    //     this.body = '';
    //   },
    // },
  };
</script>
