<template>
  <div class="wrapper">
    <div class="wrapper-content">
      <section>
        <div class="container">
          <!--app  -->

          <h1>{{ title }}</h1>

          <message v-if="message" :message="message" />

          <!-- new note -->
          <div class="new-note">
            <input type="text" v-model="note.title" />
            <textarea v-model="note.descr"> </textarea>
            <button @click="addNote">New Note</button>
          </div>

          <div class="notes">
            <div class="note" v-for="(note, index) in notes" :key="index">
              <div class="node-header">
                <p>{{ note.title }}</p>
              </div>
              <div class="note-body">
                <p>{{ note.descr }}</p>
                <p>{{ note.date }}</p>
              </div>
            </div>
          </div>
        </div>
      </section>
    </div>
  </div>
</template>
<script>
import message from '@/components/Message-error.vue';
export default {
  components: {
    message: message,
  },
  data() {
    return {
      title: 'Notes App',
      message: null,
      note: {
        title: '',
        descr: '',
      },
      notes: [
        {
          title: 'First Note',
          descr: 'Description for first note',
          date: new Date(Date.now()).toLocaleString(),
        },
        {
          title: 'Second Note',
          descr: 'Description for second note',
          date: new Date(Date.now()).toLocaleString(),
        },
        {
          title: 'Third Note',
          descr: 'Description for third note',
          date: new Date(Date.now()).toLocaleString(),
        },
      ],
    };
  },
  methods: {
    addNote() {
      //console.log(this.note);
      const { title, descr } = this.note;
      if (title === '') {
        this.message = 'Tittle can not  be empty';
        return false;
      }

      this.notes.push({
        title,
        descr,
        date: new Date(Date.now()).toLocaleString(),
      });
      this.message = null;
      this.note.descr = '';
      this.note.title = '';
    },
  },
};
</script>

<style></style>
