<template>
  <main>
    <section>
      <div
        class="message"
        v-for="comment in messages.comments"
        :key="comment.id"
      >
        <div class="comment panel" v-if="messages.comments != null">
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
            <div class="details">
              <img :src="comment.user.image.png" alt="" class="avatar" />
              <p class="username">{{ comment.user.username }}</p>
              <p class="created">{{ comment.createdAt }}</p>
            </div>
            <div class="msgcontent">
              <p class="content">{{comment.content}}</p>
            </div>
          </div>
        </div>

        <div
          class="reply panel"
          v-for="reply in comment.replies"
          :key="reply.id"
        >
          <div class="points">
            <button @click="reply.score++">
              <img src="../assets/icon-plus.svg" alt="" />
            </button>
            <div class="count">{{ reply.score }}</div>
            <button @click="reply.score--">
              <img src="../assets/icon-minus.svg" alt="" />
            </button>
          </div>
          <div class="right">
          <div class="details">
            <img :src="reply.user.image.png" alt="" class="avatar" />
            <p class="username">{{ reply.user.username }}</p>
            <p class="created">{{ reply.createdAt }}</p>
          </div>
          <div class="msgcontent">
              <p class="content">{{reply.content}}</p>
            </div></div>
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
.panel {
  background: white;

  height: fit-content;
  border-radius: 8px;
  box-shadow: 0px 0px 10px 0px rgba(0, 0, 0, 0.055);
  display: flex;
  align-items: center;
  column-gap: 1rem;
  padding: 2rem;
}
.comment {
  width: 100%;
}
.reply {
  width: 85%;
  display: flex;
  align-self: flex-end;
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
  min-width: fit-content;
  padding: 0.5rem;

  height: fit-content;
  row-gap: 1.2rem;
  border-radius: 8px;
  background-color: var(--Verylightgray);
  color: var(--Moderateblue);
  font-weight: bold;
}
.points button {
  border: none;
  background: none;
  min-width: 100%;
  padding-block: .3rem;
  cursor: pointer;
}
.avatar {
  height: 36px;
  width: auto;
}
.details {
  display: flex;
  align-items: center;
  column-gap: 1rem;
}
.created {
  color: var(--GrayishBlue);
}
.right{
  display: flex;
  flex-direction: column;
  row-gap: 1rem;
}
.content{
  text-align: left;
  color: var(--GrayishBlue);
}
.username{
  color: var(--Darkblue);
  font-weight: 500;
}
</style>
