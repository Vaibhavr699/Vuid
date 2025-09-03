<template>
  <div class="space-y-8">
    <div>
      <h1 class="text-2xl font-bold tracking-tight text-gray-800">About Page</h1>
    </div>
    
    <ReusableForm :title="formData.title" :fields="formData.fields" :submitButtonText="formData.submitButtonText" @form-submit="handleFormSubmit" />
    
    <DataTable :headers="headers" :rows="rows" :onEdit="handleEdit" :onDelete="handleDelete" />
  </div>
</template>

<script>
import DataTable from "../components/DataTable.vue";
import ReusableForm from "../components/ReusableForm.vue";

export default {
  name: "About",
  components: { DataTable, ReusableForm },
  data() {
    return {
      headers: ["ID", "Title", "Description"],
      rows: [
        { id: 1, title: "Vue.js", description: "Frontend " },
        { id: 2, title: "Node.js", description: "Backend " },
        { id: 3, title: "PostgreSQL", description: "Database" },
      ],
      formData: {
        title: "Project Information",
        submitButtonText: "Save Project",
        fields: [
          {
            name: "projectName",
            type: "text",
            label: "Project Name",
            placeholder: "Enter project name",
            required: true
          },
          {
            name: "description",
            type: "textarea",
            label: "Project Description",
            placeholder: "Describe your project",
            required: true,
            rows: 4
          },
          {
            name: "category",
            type: "select",
            label: "Category",
            placeholder: "Select project category",
            required: true,
            options: [
              { value: "web", label: "Web Development" },
              { value: "mobile", label: "Mobile App" },
              { value: "desktop", label: "Desktop Application" },
              { value: "api", label: "API Development" },
              { value: "other", label: "Other" }
            ]
          },
          {
            name: "priority",
            type: "radio",
            label: "Priority Level",
            required: true,
            options: [
              { value: "low", label: "Low" },
              { value: "medium", label: "Medium" },
              { value: "high", label: "High" },
              { value: "urgent", label: "Urgent" }
            ]
          }
        ]
      }
    };
  },
  
  methods: {
    handleEdit(row, index) {
      console.log("Edit clicked on About Page");
    },
    handleDelete(row, index) {
      console.log("Delete clicked on About Page");
    },
    handleFormSubmit(formData) {
      console.log("About Page - Form submitted:");
    }
  },
};
</script>
