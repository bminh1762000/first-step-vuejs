<template>
  <form @submit.prevent="handleSubmit">
    <div>
      <label for="name">Name</label>
      <input type="text" id="name" v-model="name" />
    </div>
    <div>
      <label for="phone">Phone</label>
      <input type="text" id="phone" v-model="phone" />
    </div>
    <div>
      <label for="name">Email</label>
      <input type="email" id="email" v-model="email" />
      <p>{{ email }}</p>
    </div>
    <div>
      <button>Add contact</button>
    </div>
  </form>
</template>

<script>
export default {
  name: "NewFriend",
  emits: ["submit-form"],
  data() {
    return {
      name: "",
      phone: "",
      email: "",
    };
  },
  methods: {
    handleSubmit() {
      this.$emit("submit-form", this.name, this.phone, this.email);
      this.name = "";
      this.phone = "";
      this.email = "";
    },
  },
};
</script>
