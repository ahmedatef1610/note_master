<template>
  <div id="app">
    <div class="container py-3">
      <div class="row">
        <div class="col-12">
          <h1 class="display-4 text-center">{{title}}</h1>
          <div class="form-group">
            <label for="title">Note Title</label>
            <input
              type="text"
              class="form-control"
              id="title"
              placeholder="Title"
              v-model="note.title"
            />
          </div>
          <div class="form-group">
            <label for="text">Note Text</label>
            <textarea class="form-control" id="text" placeholder="Text" v-model="note.text"></textarea>
          </div>
          <button class="btn btn-primary" @click="addNote">Add Note</button>
        </div>
      </div>
      <hr />
      <div class="row">
        <div class="col-12 col-md-4 mb-2" v-for="(note,i) in notes" :key="i">
          <div class="card">
            <div class="card-body">
              <button class="close" @click="removeNote(i)">&times;</button>
              <h5 class="card-title">{{note.title}}</h5>
              <h6 class="card-subtitle mb-2 text-muted">{{note.date}}</h6>
              <p class="card-text">{{note.text}}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: "Notemaster",
      note: {
        title: "",
        text: ""
      },
      notes: [
        {
          title: "visited Hawaii",
          text: "I love the Beaches and delicious fresh coconuts",
          date: new Date(Date.now()).toLocaleString()
        }
      ]
    };
  },
  methods: {
    addNote() {
      this.notes.push({
        ...this.note,
        date: new Date(Date.now()).toLocaleString()
      });
      this.note.title = "";
      this.note.text = "";
    },
    removeNote(i) {
      this.notes.splice(i, 1);
    }
  }
};
</script>

<style lang="scss">
.card-text {
  white-space: pre-wrap;
}
</style>
