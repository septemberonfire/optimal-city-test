<script setup>

</script>

<template>
  <v-card variant="outlined" class="container">
    <div class="interlocutor">
      <img src="./assets/ROBOT.jpg" alt="robot avatar" class="bot-avatar">
      <h3>Simple VueJS Bot</h3>
    </div>
    <div class="dialog">
      <div class="bot-message">
        Hello!
      </div>
      <div class="user-message">
        I want pizza...
      </div>
      <div class="bot-message">
        Got it! Anything else?
      </div>
    </div>
  </v-card>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  gap: 12px;
  width: 300px;
  padding: 20px;
}

.interlocutor {
  display: flex;
  justify-content: flex-start;
  align-items: center;
  gap: 12px;
}

.bot-avatar {
  width: 80px;
  border: 1px solid aquamarine;
  border-radius: 50%;
}

.bot-message {
  background-color: aquamarine;
  align-items: flex-start;
  border-radius: 8px;
  width: fit-content;
  padding: 12px 16px;
}

.user-message {
  background-color: aqua;
  border-radius: 8px;
  width: fit-content;
  padding: 12px 16px;
  align-self: flex-end;
}
</style>
