<template>
  <main>
    <section>
      <div
        class="message"
        v-for="comment in messages.comments"
        :key="comment.id"
      >
        <div class="comment panel" v-if="messages.comments != null" ref="commentpanel">
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
            <div class="msgtop">
              <span class="details">
              <img :src="comment.user.image.png" alt="" class="avatar" />
              <p class="username">{{comment.user.username }}</p>
              <p class="created">{{ comment.createdAt }}</p>
            </span>
            <button v-show="comment.user.username != messages.currentUser.username" class="replybtn"><img src="../assets/icon-reply.svg" alt=""> Reply</button>
            <div v-show="comment.user.username === messages.currentUser.username" class="crudbuttons">
            <button class="deletebtn"><img src="../assets/icon-delete.svg" alt="" @click="deleteComment()"> Delete</button>
            <button class="editbtn"><img src="../assets/icon-edit.svg" alt=""> Edit</button>
          </div>
            </div>
            <div class="msgcontent">
              <p class="content">{{ comment.content }}</p>
            </div>
          </div>
        </div>

        <div
          class="reply panel"
          v-for="reply in comment.replies"
          :key="reply.id"
          ref="replypanel"
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
            <div class="msgtop">
              <span class="details">
              <img :src="reply.user.image.png" alt="" class="avatar" />
              <p class="username">{{ reply.user.username }}</p>
              <p class="created">{{ reply.createdAt }}</p>
            </span>
            <button v-if="reply.user.username != messages.currentUser.username" class="replybtn"><img src="../assets/icon-reply.svg" alt=""> Reply</button>
            <div v-if="reply.user.username === messages.currentUser.username" class="crudbuttons">
            <button class="deletebtn"><img src="../assets/icon-delete.svg" alt="" > Delete</button>
            <button class="editbtn"><img src="../assets/icon-edit.svg" alt=""> Edit</button>
          </div>
            
            
            </div>
            <div class="msgcontent">
              <p class="content"><p class="at">{{ "@" + reply.replyingTo + ' ' + reply.content}}</p> {{  }}</p>
            </div>
          </div>
        </div>
      </div>
      <div class="panel textbox">
        <img :src="messages.currentUser.image.png" alt="" class="cUserImage" />
        <textarea
          name=""
          id="textarea"
          placeholder="Add a comment..."
          v-model="textmessage"
        ></textarea>
        <button @click="sendComment()" @keypress.enter="sendComment()">SEND</button>
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
      textmessage: "",
    };
  },
   methods: {
    sendComment() {
       this.messages.comments.push({   
      id: this.messages.comments.length + 3,
      content: this.textmessage,
      createdAt: "just now",
      score: 0,
      user: {
        image: { 
          png: this.messages.currentUser.image.png,
          webp: "./images/avatars/image-amyrobson.webp"
        },
        username: this.messages.currentUser.username
      },
      replies: []
       })
       this.textmessage = '';
     },
     deleteComment() {
   
  }
    }
  }
</script>
<style scoped>
main {
  background-color: hsl(228, 33%, 97%);
  width: 100%;
  height: fit-content;
  display: flex;
  justify-content: center;
  align-items: center;
  padding-block: 6rem;
}
section {
  width: 45rem;
  height: fit-content;
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

  column-gap: 1rem;
  padding: 2rem;
}
.comment {
  width: 100%;
  align-items: center;
}
.reply {
  width: 85%;
  display: flex;
  align-self: flex-end;
  align-items: center;
}
.textbox {
  width: 100%;
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
  padding-block: 0.3rem;
  cursor: pointer;
}
.avatar {
  height: 36px;
  width: auto;
}
.msgtop {
  display: flex;
  align-items: center;
  justify-content: space-between;
  column-gap: 1rem;
  width: 100%;
}
.msgtop button{
  background: none;
  outline: none;
  border: none;
  display: flex;
  align-items: center;column-gap: .4rem;
  color: var(--Moderateblue);
  font-weight: 500;
}
.deletebtn{
  color: var(--SoftRed) !important;
}
.crudbuttons{
  display: flex;
  column-gap: 1rem;
}
.details{
  display: flex;
  align-items: center;
  column-gap: 1rem;
}
.created {
  color: var(--GrayishBlue);
}
.right {
  display: flex;
  flex-direction: column;
  row-gap: 1rem;
  width: 100%;
}
.content {
  text-align: left;
  color: var(--GrayishBlue);
}
.username {
  color: var(--Darkblue);
  font-weight: 500;
}
.cUserImage {
  width: 43px;
  height: 43px;
}
#textarea {
  width: 30rem;
  height: 6rem;
  resize: none;
  border: 2px solid var(--Lightgray);
  border-radius: 6px;
  padding-left: 1rem;
  padding-top: 0.5rem;
  color: var(--GrayishBlue);
  font-size: 1rem;
  outline: none;
}
#textarea:focus{
  border: 2px solid var(--Lightgrayishblue);
}
.textbox button{
  background: var(--Moderateblue);
  border: none;
  outline: none;
  height: fit-content;
  width: fit-content;
  color: var(--White);
  padding-inline: 1.7rem;
  padding-block: .6rem;
  border-radius: 8px;
  transition: ease .2s all;

}
.textbox button:hover{
  opacity: .8;
}
button:hover{
   opacity: .8;
}
</style>
