<template>
  <div>
    <h2>Book</h2>
    <form>
      <div class="md-4">
        <label for="title" class="form-label">Title</label>
        <input type="text" v-model="bookTitle" class="form-control" />
        <p v-if="errorTitleFlg" class="text-danger">空白では登録できません</p>
      </div>
      <div class="md-4 mt-3 mb-5">
        <label for="thought" class="form-label">Thooughts</label>
        <textarea v-model="bookThoughts" class="form-control"></textarea>
        <p v-if="errorThoughtsFlg" class="text-danger">
          空白では登録できません
        </p>
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
  errorTitleFlg: boolean;
  errorThoughtsFlg: boolean;
};

export default defineComponent({
  name: "InputBookInfo",
  data(): bookInfo {
    return {
      bookTitle: "",
      bookThoughts: "",
      errorTitleFlg: false,
      errorThoughtsFlg: false,
    };
  },
  methods: {
    addBookInfo() {
      this.errorTitleFlg = false;
      this.errorThoughtsFlg = false;
      if (!this.bookTitle.trim()) this.errorTitleFlg = true;
      if (!this.bookThoughts.trim()) this.errorThoughtsFlg = true;
      if (this.errorTitleFlg === false && this.errorThoughtsFlg === false) {
        this.$emit("addBookInfo", this.bookTitle, this.bookThoughts);
        this.bookTitle = "";
        this.bookThoughts = "";
      }
    },
  },
});
</script>
