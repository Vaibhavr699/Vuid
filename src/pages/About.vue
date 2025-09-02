<template>
  <div class="space-y-4">
    <div>
      <h1 class="text-2xl font-bold tracking-tight text-gray-800">About Page</h1>
    </div>
    <DataTable :headers="headers" :rows="rows" :onEdit="handleEdit" :onDelete="handleDelete" />
  </div>
</template>

<script>
import DataTable from "../components/DataTable.vue";

export default {
  name: "About",
  components: { DataTable },
  data() {
    return {
      headers: ["ID", "Title", "Description"],
      rows: [
        { id: 1, title: "Vue.js", description: "Frontend " },
        { id: 2, title: "Node.js", description: "Backend " },
        { id: 3, title: "PostgreSQL", description: "Database" },
      ],
    };
  },
  methods: {
    handleEdit(row, index) {
      console.log("Edit clicked on About Page");
    },
    handleDelete(row, index) {
      console.log("Delete clicked on About Page");
    },
  },
};
</script>
