<template>
  <div class="user-input">
    <input
      type="text"
      class="user-input__input"
      id="user-input"
      name="userInput"
      v-model="userInput"
    />
    <div v-show="userInput" class="user-input__output-message">
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
      const convertedInput = this.userInput.split(" ").join("").toLowerCase();
      return convertedInput.length >= 3
        ? convertedInput ===
            convertedInput.toLowerCase().split("").reverse().join("")
        : false;
    },
  },
  watch: {
    isPalindrome(value) {
      if (
        value &&
        !this.allPalindromes.includes(this.userInput.toLowerCase())
      ) {
        this.$emit("savePalindrome", this.userInput);
      }
    },
  },
};
</script>
