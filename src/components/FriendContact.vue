<template>
  <li>
    <h2>{{ name }}{{ isFavorite ? "(Favorite)" : "" }}</h2>
    <button @click="showDetails">
      {{ detailsAreVisible ? "Show Details" : "Hide" }}
    </button>
    <button @click="toggleFavorite">
      {{ isFavorite ? "Favorite" : "Hide" }}
    </button>
    <ul v-if="detailsAreVisible">
      <li><strong>Phone:</strong> {{ phoneNumber }}</li>
      <li><strong>Email:</strong> {{ emailAddress }}</li>
    </ul>
    <button @click="deleteFriend" style="display: block; margin: 1rem auto">
      Delete Contact
    </button>
  </li>
</template>

<script>
export default {
  name: "FriendContact",
  emits: {
    toggleFavorite: function(id) {
      if (id) {
        return true;
      }
      return false;
    },
    "delete-contact": function(id) {
      if (id) {
        return true;
      }
      return false;
    },
  },
  data() {
    return {
      detailsAreVisible: false,
    };
  },
  methods: {
    showDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    toggleFavorite() {
      this.$emit("toggleFavorite", this.id);
    },
    deleteFriend() {
      this.$emit("delete-contact", this.id);
    },
  },
  props: {
    id: {
      type: String,
      required: true,
    },
    name: {
      type: String,
      required: true,
    },
    phoneNumber: {
      type: String,
      required: true,
    },
    emailAddress: {
      type: String,
      required: true,
    },
    isFavorite: {
      type: Boolean,
      required: true,
    },
  },
};
</script>
