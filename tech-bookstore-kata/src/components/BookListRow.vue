<template>
  <td class="table-item__table">{{ tdtitle }}</td>
  <td class="table-item__table">{{ tdisbn }}</td>
  <td class="table-item__table">
    <BaseButton
      v-on:bookmarkedClicked="bookmarkClicked"
      :buttonClass="ButtonClass"
      :text="text"
    />
  </td>
</template>

<script>
import BaseButton from "@/components/BaseButton.vue";

export default {
  name: "BookListRow",
  props: { tdtitle: { type: String }, tdisbn: { type: String } },
  components: {
    BaseButton,
  },
  data() {
    return {
      primary: true,
      ButtonClass: "btn--primary",
      text: "Add Bookmark",
    };
  },
  methods: {
    bookmarkClicked(btn) {
      btn.isBookmarked = !btn.isBookmarked;
      if (btn.isBookmarked === false) {
        this.text = "Add Bookmark";
      } else {
        this.text = "Remove Bookmark";
      }
    },
  },
};
</script>

<style scoped>
.table-item__table {
  padding: 12px 15px;
}
</style>
