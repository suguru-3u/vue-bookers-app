<template>
  <h2>Books</h2>
  <table class="table">
    <thead>
      <tr>
        <th>ID</th>
        <th>Title</th>
        <th></th>
      </tr>
    </thead>
    <tbody v-for="bookinfo in bookInfoArray" v-bind:key="bookinfo.id">
      <tr>
        <td>
          {{ bookinfo.id }}
        </td>
        <td>
          {{ bookinfo.title }}
        </td>
        <td v-on:click="editBook(bookinfo.id)">編集</td>
      </tr>
    </tbody>
  </table>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  props: ["bookInfoArray"],
  methods: {
    editBook(id: string) {
      this.$emit("editBook", id);
    },
  },
});
</script>
