<template>
  <div class="user-input">
    <input type="text" id="user-input" name="userInput" v-model="userInput" />
    <div v-show="userInput">
      <p v-if="isPalindrome">
        "{{ userInput }}"
        <span class="user-input__output-message--green">is</span> palindrom!
      </p>
      <p v-else>
        "{{ userInput }}"
        <span class="user-input__output-message--red">is not</span> palindrom!
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: "UserInput",
  props: ["allPalindromes"],
  data() {
    return {
      userInput: "",
    };
  },
  computed: {
    isPalindrome() {
      return this.userInput.length >= 3
        ? this.userInput === this.userInput.split("").reverse().join("")
        : false;
    },
  },
  watch: {
    isPalindrome(value) {
      if (value && !this.allPalindromes.includes(this.userInput)) {
        this.$emit("savePalindrome", this.userInput);
      }
    },
  },
};
</script>
