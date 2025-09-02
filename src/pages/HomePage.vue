<template>
  <div class="space-y-4">
    <div>
      <h1 class="text-2xl font-bold tracking-tight text-gray-800">Home Page</h1>
    </div>
    <DataTable :headers="headers" :rows="rows" :onEdit="handleEdit" :onDelete="handleDelete" />
  </div>
 </template>

<script>
import DataTable from "../components/DataTable.vue";

export default {
  name: "Home",
  components: { DataTable },
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
    };
  },
  methods: {
    handleEdit(row, index) {
      console.log("Edit clicked on Home Page");
    },
    handleDelete(row, index) {
      console.log("Delete clicked on Home Page");
    },
  },
};
</script>
