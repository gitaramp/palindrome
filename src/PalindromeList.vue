<template>
  <ul
    v-if="allPalindromes.length > 0"
    class="palindrome-list"
    title="Znalezione palindromy"
  >
    <li v-for="palindrome in allPalindromes" :key="palindrome">
      {{ palindrome }}
    </li>
  </ul>
</template>

<script>
export default {
  name: "PalindromeList",
  props: ["allPalindromes"],
};
</script>
