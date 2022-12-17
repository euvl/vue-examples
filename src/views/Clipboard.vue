<template>
  <div class="home">
    <button v-clipboard="'One'">Test #1</button>
    <button v-clipboard="two">Test #2</button>
    <button @click="copyWithPlugin">Test #3</button>
    <button @click="copyWithoutPlugin">Test #4</button>
  </div>
</template>

<script lang="ts">
import { Clipboard } from "v-clipboard";
import { Options, Vue } from "vue-class-component";

@Options({
  data() {
    return {
      two: "Two",
    };
  },
  methods: {
    async copyWithPlugin() {
      this.$clipboard("Three");
    },

    async copyWithoutPlugin() {
      await Clipboard.copy("Four");
    },
  },
})
export default class ClipboardView extends Vue {}
</script>
