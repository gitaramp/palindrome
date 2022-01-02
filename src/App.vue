<template>
  <div id="app">
    <UserInput
      :allPalindromes="allPalindromes"
      @savePalindrome="savePalindrome"
    />
    <PalindromeList :allPalindromes="allPalindromes" />
  </div>
</template>

<script>
import UserInput from "./UserInput.vue";
import PalindromeList from "./PalindromeList.vue";

export default {
  name: "App",
  components: {
    UserInput,
    PalindromeList,
  },
  data() {
    return {
      allPalindromes: [],
    };
  },
  mounted() {
    this.allPalindromes = JSON.parse(localStorage.getItem("palindromes")) || [];
  },
  methods: {
    savePalindrome(newPalindrome) {
      this.allPalindromes.push(newPalindrome);
      localStorage.setItem("palindromes", JSON.stringify(this.allPalindromes));
    },
  },
};
</script>
