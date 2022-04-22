<template>
  <div>
    <h2>Book</h2>
    <form action="">
      <div class="md-4">
        <label for="title" class="form-label">Title</label>
        <input type="text" v-model="bookTitle" class="form-control" />
      </div>
      <div class="md-4 mt-3 mb-5">
        <label for="thought" class="form-label">Thooughts</label>
        <textarea v-model="bookThoughts" class="form-control"></textarea>
      </div>
      <button type="button" class="btn btn-success" v-on:click="addBookInfo">
        create
      </button>
    </form>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

type bookInfo = {
  bookTitle: string;
  bookThoughts: string;
};

export default defineComponent({
  name: "InputBookInfo",
  data(): bookInfo {
    return {
      bookTitle: "",
      bookThoughts: "",
    };
  },
  methods: {
    addBookInfo() {
      this.$emit("addBookInfo", this.bookTitle, this.bookThoughts);
      this.bookTitle = "";
      this.bookThoughts = "";
    },
  },
});
</script>
