<template>
  <div class="container">
    <div class="row">
      <div class="col-md-4">
        <InputBookInfo @addBookInfo="addBookInfo" />
      </div>
      <div class="col-md-8">
        <IndexBooks v-bind:bookInfoArray="bookInfoArray" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import InputBookInfo from "@/components/InputBookInfo.vue"; // @ is an alias to /src
import IndexBooks from "@/components/IndexBooks.vue"; // @ is an alias to /src

type booksInfo = {
  bookInfoArray: bookInfoObj[];
};

type bookInfoObj = {
  id: string;
  title: string;
  thooughts: string;
};

export default defineComponent({
  name: "Home",
  components: {
    InputBookInfo,
    IndexBooks,
  },
  data(): booksInfo {
    return {
      bookInfoArray: [],
    };
  },
  methods: {
    addBookInfo(title: string, thooughts: string) {
      this.bookInfoArray.push({
        id: String(this.bookInfoArray.length + 1),
        title: title,
        thooughts: thooughts,
      });
    },
  },
});
</script>
