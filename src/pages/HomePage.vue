<template>
  <div class="space-y-8">
    <div>
      <h1 class="text-2xl font-bold tracking-tight text-gray-800">Home Page</h1>
    </div>
    
    <ReusableForm :title="formData.title" :fields="formData.fields" :submitButtonText="formData.submitButtonText" @form-submit="handleFormSubmit" />

    <DataTable :headers="headers" :rows="rows" :onEdit="handleEdit" :onDelete="handleDelete" />


  </div>
 </template>

<script>
import DataTable from "../components/DataTable.vue";
import ReusableForm from "../components/ReusableForm.vue";

export default {
  name: "Home",
  components: { DataTable, ReusableForm },
  data() {
    return {
      headers: ["ID", "Name", "Role"],
      rows: [
        { id: 1, name: "Rahul", role: "Developer" },
        { id: 2, name: "Kapil", role: "Designer" },
        { id: 3, name: "Rahul", role: "Developer" },
        { id: 4, name: "Kapil", role: "Designer" },
        { id: 5, name: "Rahul", role: "Developer" },
        { id: 6, name: "Kapil", role: "Designer" },
      ],
      formData: {
        title: "User Registration",
        submitButtonText: "Register User",
        fields: [
          {
            name: "firstName",
            type: "text",
            label: "First Name",
            placeholder: "Enter your first name",
            required: true
          },
          {
            name: "lastName",
            type: "text",
            label: "Last Name",
            placeholder: "Enter your last name",
            required: true
          },
          {
            name: "email",
            type: "email",
            label: "Email Address",
            placeholder: "Enter your email",
            required: true
          },
          {
            name: "age",
            type: "number",
            label: "Age",
            placeholder: "Enter your age",
            required: true
          },
          
        ]
      }
    };
  },
  methods: {
    handleEdit(row, index) {
      console.log("Edit clicked on Home Page");
    },
    handleDelete(row, index) {
      console.log("Delete clicked on Home Page");
    },
    handleFormSubmit(formData) {
      console.log("Home Page - Form submitted:");
    }
  },
};
</script>
