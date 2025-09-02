<template>
  <div
    class="overflow-x-auto bg-white shadow-sm ring-1 ring-gray-200 rounded-lg"
  >
    <table class="w-full border-collapse text-sm">
      <thead class="bg-gray-50">
        <tr>
          <th
            v-for="header in headers"
            :key="header"
            class="text-left px-4 py-3 font-semibold text-gray-700"
          >
            {{ header }}
          </th>
          <th class="text-left px-4 py-3 font-semibold text-gray-700">
            Actions
          </th>
        </tr>
      </thead>
      <tbody class="divide-y divide-gray-100">
        <tr
          v-for="(row, rowIndex) in rows"
          :key="rowIndex"
          class="even:bg-gray-50/60 hover:bg-blue-50/60"
        >
          <td
            v-for="(value, key) in row"
            :key="key"
            class="px-4 py-2 text-gray-700"
          >
            {{ value }}
          </td>
          <td class="px-4 py-2 whitespace-nowrap flex items-center gap-2">
            <button
              type="button"
              class="inline-flex items-center rounded-md bg-blue-600 px-3 py-1.5 text-white text-xs font-medium hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500"
              @click="onEdit && onEdit(row, rowIndex)"
            >
              Edit
            </button>
            <button
              type="button"
              class="inline-flex items-center rounded-md bg-rose-600 px-3 py-1.5 text-white text-xs font-medium hover:bg-rose-700 focus:outline-none focus:ring-2 focus:ring-rose-500"
              @click="onDelete && onDelete(row, rowIndex)"
            >
              Delete
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
  <div
    v-if="!rows || rows.length === 0"
    class="text-center text-gray-500 text-sm py-4"
  >
    No data available
  </div>
</template>

<script>
export default {
  name: "DataTable",
  props: {
    headers: Array,
    rows: Array,
    onEdit: Function,
    onDelete: Function,
  },
};
</script>
