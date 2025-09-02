<template>
  <div class="space-y-4">
    <div>
      <h1 class="text-2xl font-bold tracking-tight text-gray-800">Contact Page</h1>
    </div>
    <DataTable :headers="headers" :rows="rows" :onEdit="handleEdit" :onDelete="handleDelete" />
  </div>
</template>

<script>
import DataTable from "../components/DataTable.vue";

export default {
  name: "Contact",
  components: { DataTable },
  data() {
    return {
      headers: ["ID", "Name", "Email", "Phone"],
      rows: [
        { id: 1, name: "Hello", email: "hello@example.com", phone: "1234567890" },
        { id: 2, name: "Kapil", email: "Kapil@example.com", phone: "9876543210" },
        { id: 3, name: "Charlie", email: "charlie@example.com", phone: "5555555555" },
        { id: 4, name: "David", email: "david@example.com", phone: "1112223333" },
      ],
    };
  },
  methods: {
    handleEdit(row, index) {
      console.log("Edit clicked on Contact Page");
    },
    handleDelete(row, index) {
      console.log("Delete clicked on Contact Page");
    },
  },
};
</script>
