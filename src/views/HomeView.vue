<template>
  <main>
    <section>
      <div
        class="message"
        v-for="comment in messages.comments"
        :key="comment.id"
      >
        <div class="comment" v-if="messages.comments != null">
          <div class="points">
            <button @click="comment.score++">
              <img src="../assets/icon-plus.svg" alt="" />
            </button>
            <div class="count">{{ comment.score }}</div>
            <button @click="comment.score--">
              <img src="../assets/icon-minus.svg" alt="" />
            </button>
          </div>
          <div class="right">
            <div class="details" v-for="user in comment" :key="user.username">
              <img :src="comment.user.image.png" alt="" />
              <p class="username">{{ user.username }}</p>
            </div>
            <div class="msgcontent">
              <p>{{}}</p>
            </div>
          </div>
        </div>

        <div class="reply" v-for="reply in comment.replies" :key="reply.id">
          {{ reply.id }}
        </div>
      </div>
    </section>
  </main>
</template>

<script>
// @ is an alias to /src
import messageData from "/data/data.json";

export default {
  name: "HomeView",
  data() {
    return {
      messages: messageData,
    };
  },
};
</script>
<style scoped>
main {
  background-color: hsl(228, 33%, 97%);
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
section {
  width: 45rem;
  height: 90vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  row-gap: 1.5rem;
}
.comment {
  background: white;
  width: 100%;
  height: 10rem;
  border-radius: 8px;
  box-shadow: 0px 0px 10px 0px rgba(0, 0, 0, 0.055);
  display: flex;
  align-items: center;
}
.reply {
  background: white;
  height: 10rem;
  width: 85%;
  display: flex;
  align-self: flex-end;
  border-radius: 8px;
  box-shadow: 0px 0px 10px 0px rgba(0, 0, 0, 0.055);
}
.message {
  display: flex;
  flex-direction: column;

  width: 100%;
  height: fit-content;
  row-gap: 1.5rem;

  align-items: center;
}
.points {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: fit-content;
  padding: 0.5rem;
  padding-block: 1rem;
  margin-left: 1.8rem;

  height: fit-content;
  row-gap: 1rem;
  border-radius: 4px;
  background-color: var(--Verylightgray);
  color: var(--Moderateblue);
  font-weight: bold;
}
.points button {
  border: none;
  background: none;
}
</style>
