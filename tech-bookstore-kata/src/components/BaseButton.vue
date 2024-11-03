<template>
  <button v-on:click="$emit('bookmarkedClicked', this)" :class="buttonClass">
    {{ text }}
  </button>
</template>

<script>
export default {
  name: "BaseButton",
  props: {
    text: {
      String,
      validator: (value) => ["Add Bookmark", "Remove Bookmark"].includes(value),
      default: "Add Bookmark",
    },
    buttonClass: {
      type: String,
      validator: (value) => ["btn--primary", "btn--secondary"].includes(value),
      default: "btn--primary",
    },
  },
  data() {
    return {
      isBookmarked: false,
    };
  },
  methods: {},
};
</script>
<style scoped>
.btn {
  border: 3px solid transparent;
  border-radius: 3px;
  padding: 5px;
  cursor: pointer;
}

.btn--primary {
  border-color: var(--primary-dark);
  background-color: var(--primary);
  color: #fff;
}

.btn--primary:hover {
  border-color: var(--primary);
  background-color: var(--primary-dark);
}

.btn--secondary {
  border-color: var(--primary);
  background-color: transparent;
  color: var(--primary);
}

.btn--secondary:hover {
  background-color: var(--primary);
  color: #fff;
}
</style>
