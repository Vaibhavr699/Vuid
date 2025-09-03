<template>
  <div class="space-y-8">
    <div>
      <h1 class="text-2xl font-bold tracking-tight text-gray-800">Contact Page</h1>
    </div>
    
    <ReusableForm :title="formData.title" :fields="formData.fields" :submitButtonText="formData.submitButtonText" @form-submit="handleFormSubmit" />
    
    <DataTable :headers="headers" :rows="rows" :onEdit="handleEdit" :onDelete="handleDelete" />
  </div>
</template>

<script>
import DataTable from "../components/DataTable.vue";
import ReusableForm from "../components/ReusableForm.vue";

export default {
  name: "Contact",
  components: { DataTable, ReusableForm },
  data() {
    return {
      headers: ["ID", "Name", "Email", "Phone"],
      rows: [
        { id: 1, name: "Hello", email: "hello@example.com", phone: "1234567890" },
        { id: 2, name: "Kapil", email: "Kapil@example.com", phone: "9876543210" },
        { id: 3, name: "Charlie", email: "charlie@example.com", phone: "5555555555" },
        { id: 4, name: "David", email: "david@example.com", phone: "1112223333" },
      ],
      formData: {
        title: "Contact Us",
        submitButtonText: "Send Message",
        fields: [
          {
            name: "fullName",
            type: "text",
            label: "Full Name",
            placeholder: "Enter your full name",
            required: true
          },
          {
            name: "email",
            type: "email",
            label: "Email Address",
            placeholder: "Enter your email address",
            required: true
          },
          {
            name: "phone",
            type: "text",
            label: "Phone Number",
            placeholder: "Enter your phone number",
            required: false
          },
          {
            name: "subject",
            type: "select",
            label: "Subject",
            placeholder: "Select a subject",
            required: true,
            options: [
              { value: "general", label: "General Inquiry" },
              { value: "support", label: "Technical Support" },
              { value: "sales", label: "Sales Question" },
              { value: "feedback", label: "Feedback" },
              { value: "other", label: "Other" }
            ]
          },
          {
            name: "message",
            type: "textarea",
            label: "Message",
            placeholder: "Enter your message here",
            required: true,
            rows: 5
          }
        ]
      }
    };
  },
  methods: {
    handleEdit(row, index) {
      console.log("Edit clicked on Contact Page");
    },
    handleDelete(row, index) {
      console.log("Delete clicked on Contact Page");
    },
    handleFormSubmit(formData) {
      console.log("Contact Page - Form submitted:");
    }
  },
};
</script>
