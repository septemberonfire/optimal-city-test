<script>
export default {
  data() {
    return {
      messages: [
        {
          owner: "bot-message",
          content: "Привет! Что я могу сделать для вас?",
          id: 0,
        },
      ],
      loading: false,
    };
  },
  methods: {
    buyPizza() {
      this.messages.push({
        owner: "user-message",
        content: "Заказать пиццу",
        id: new Date(),
      });

      this.loading = true

      setTimeout(() => {
        this.messages.push({
          owner: "bot-message",
          content: "Хорошо, я закажу для вас пиццу. Что-нибудь ещё?",
          id: new Date(),
        });
        this.loading = false
      }, 2000);
    },
    tellAJoke() {
      this.messages.push({
        owner: "user-message",
        content: "Рассказать шутку",
        id: new Date(),
      });

      this.loading = true

      setTimeout(() => {
        this.messages.push({
          owner: "bot-message",
          content: "Хорошо, я расскажу шутку. Что-нибудь ещё?",
          id: new Date(),
        });
        this.loading = false
      }, 2000);
    },
    showWeather() {
      this.messages.push({
        owner: "user-message",
        content: "Отобразить погоду",
        id: new Date(),
      });

      this.loading = true
      setTimeout(() => {
        this.messages.push({
          owner: "bot-message",
          content:
            "Хорошо, я отображу погоду на данный момент. Что-нибудь ещё?",
          id: new Date(),
        });
        this.loading = false
      }, 2000);
    },
  },

  watch: {
    messages: {
      handler() {
        const container = this.$el.querySelector(".dialog");
        this.$nextTick(() => {
          container.scrollTop = container.scrollHeight;
        });
      },
      deep: true,
    },
  },
};
</script>

<template>
  <v-card variant="outlined" elevation="16" class="container">
    <div class="interlocutor">
      <img src="./assets/ROBOT.jpg" alt="robot avatar" class="bot-avatar" />
      <h3>Simple VueJS Bot</h3>
    </div>
    <div class="dialog">
      <div v-for="el in messages" :key="el.id" :class="el.owner">
        {{ el.content }}
      </div>
      <div v-if="loading" class="loader"></div>
    </div>
    <div class="btns">
      <v-btn @click="buyPizza"> Заказать пиццу </v-btn>
      <v-btn @click="tellAJoke"> Рассказать шутку </v-btn>
      <v-btn @click="showWeather"> Отобразить погоду </v-btn>
    </div>
  </v-card>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  gap: 12px;
  max-width: 400px;
  padding: 20px;
}

@media screen and (min-width: 320px) {
}

.interlocutor {
  display: flex;
  justify-content: flex-start;
  align-items: center;
  gap: 12px;
}

.bot-avatar {
  width: 60px;
  border: 1px solid aquamarine;
  border-radius: 50%;
}

.dialog {
  display: flex;
  flex-direction: column;
  gap: 16px;
  border: 1px solid aquamarine;
  border-radius: 8px;
  padding: 12px;
  overflow-y: scroll;
  height: 200px;
  scrollbar-width: thin;
  scroll-behavior: smooth;
}

::-webkit-scrollbar {
  width: 10px;
}

/* Track */
::-webkit-scrollbar-track {
  background: #f1f1f1;
  border-radius: 100px;
}

/* Handle */
::-webkit-scrollbar-thumb {
  background: rgb(13, 235, 235);
  border-radius: 100px;
}

/* Handle on hover */
::-webkit-scrollbar-thumb:hover {
  background: rgb(9, 196, 196);
}

.bot-message {
  background-color: aquamarine;
  align-items: flex-start;
  border-radius: 8px;
  width: fit-content;
  padding: 12px 16px;
  max-width: 80%;
  text-align: left;
}

.user-message {
  background-color: aqua;
  border-radius: 8px;
  width: fit-content;
  padding: 12px 16px;
  align-self: flex-end;
  max-width: 80%;
  text-align: right;
}

.btns {
  display: flex;
  flex-direction: column;
  gap: 12px;
}

/* HTML: <div class="loader"></div> */
.loader {
  width: 60px;
  min-height: 20px;
  aspect-ratio: 2;
  --_g: no-repeat radial-gradient(circle closest-side, aquamarine 90%, #0000);
  background: var(--_g) 0% 50%, var(--_g) 50% 50%, var(--_g) 100% 50%;
  background-size: calc(100% / 3) 50%;
  animation: l3 1s infinite linear;
}
@keyframes l3 {
  20% {
    background-position: 0% 0%, 50% 50%, 100% 50%;
  }
  40% {
    background-position: 0% 100%, 50% 0%, 100% 50%;
  }
  60% {
    background-position: 0% 50%, 50% 100%, 100% 0%;
  }
  80% {
    background-position: 0% 50%, 50% 50%, 100% 100%;
  }
}
</style>
