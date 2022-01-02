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
  data() {
    return {
      userInput: "",
    };
  },
  computed: {
    isPalindrome() {
      return this.userInput === this.userInput.split("").reverse().join("");
    },
  },
};
</script>
