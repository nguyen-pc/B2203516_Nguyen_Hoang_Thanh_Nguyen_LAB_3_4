<template>
  <div class="page">
    <h4>Tạo mới liên hệ</h4>
    <ContactForm :contact="contact" @submit:contact="addContact" />
    <p>{{ message }}</p>
  </div>
</template>
<script>
import ContactForm from "@/components/ContactForm.vue";
import ContactService from "@/services/contact.service";
export default {
  components: {
    ContactForm,
  },

  data() {
    return {
      contact: {},
      message: "",
    };
  },
  methods: {
    async addContact(data) {
      try {
        await ContactService.create(data);
        alert("Tạo mới liên hệ thành công");
      } catch (e) {
        console.log(e);
      }
    },
  },
};
</script>
