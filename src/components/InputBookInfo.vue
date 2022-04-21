<template>
  <div>
    {{ $data }}
    <h2>Book</h2>
    <label for="title">Title</label>
    <input type="text" v-model="bookTitle" /><br />
    <label for="thought">Thooughts</label>
    <textarea cols="60" rows="10" v-model="bookThoughts"></textarea><br />
    <button type="button" class="btn btn-success" v-on:click="addBookInfo">
      create</button
    ><br />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

type bookInfo = {
  bookTitle: string;
  bookThoughts: string;
  // bookInfoArray: bookInfoObj[];
};

// type bookInfoObj = {
//   title: string;
//   thooughts: string;
// };

export default defineComponent({
  name: "InputBookInfo",
  data(): bookInfo {
    return {
      bookTitle: "",
      bookThoughts: "",
      // bookInfoArray: [],
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
