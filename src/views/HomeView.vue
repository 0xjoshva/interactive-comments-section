<template>
  <main>
    <section>
      <div class="message" v-for="comment in messages.comments" :key="comment.id">
      <div class="comment" v-if="messages.comments != null">
        <div class="points">
        <button><img src="../assets/icon-plus.svg" alt=""></button>
        <div class="count">1</div>
        <button><img src="../assets/icon-minus.svg" alt=""></button>
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
.comment{
background: white;
  width: 100%;
  height: 10rem;
  border-radius: 8px;
  box-shadow: 0px 0px 10px 0px rgba(0, 0, 0, 0.055);
}
.reply{
  background: white;
  height: 10rem;
  width: 85%;
  display: flex;
  align-self: flex-end;
  border-radius: 8px;
  box-shadow: 0px 0px 10px 0px rgba(0, 0, 0, 0.055);
}
.message{
  display: flex;
  flex-direction: column;

  width: 100%;
  height:fit-content;
  row-gap: 1.5rem;
}
.points{
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: fit-content;
  padding: .5rem;
  padding-block: 1rem;

  height: fit-content;
  row-gap: 1rem;
  border-radius: 4px;
  background-color:var(--Verylightgray);
}
.points button{
  border: none;
  background: none;

}
</style>
