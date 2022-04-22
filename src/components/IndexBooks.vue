<template>
  <h1>Books</h1>
  <table class="table">
    <thead>
      <tr>
        <th>ID</th>
        <th>Title</th>
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
      </tr>
    </tbody>
  </table>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  props: ["bookInfoArray"],
});
</script>
