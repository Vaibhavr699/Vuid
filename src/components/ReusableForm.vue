<template>
  <div class="max-w-md mx-auto bg-white p-6 rounded-lg shadow-md">

    <form v-on:submit.prevent="handleSubmit" class="space-y-4">
      <div v-for="field in fields" :key="field.name" class="space-y-2">
        <label
          :for="field.name"
          class="block text-sm font-medium text-gray-700"
        >
          {{ field.label }}
        </label>

        <input
          v-if="field.type === 'text' || field.type === 'email'"
          :type="field.type"
          :id="field.name"
          :name="field.name"
          v-model="formData[field.name]"
          :placeholder="field.placeholder"
          :required="field.required"
          class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-transparent"
        />

        <input
          v-else-if="field.type === 'number'"
          :type="field.type"
          :id="field.name"
          :name="field.name"
          v-model.number="formData[field.name]"
          :placeholder="field.placeholder"
          :required="field.required"
          class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-transparent"
        />

        <textarea
          v-else-if="field.type === 'textarea'"
          :id="field.name"
          :name="field.name"
          v-model="formData[field.name]"
          :placeholder="field.placeholder"
          :required="field.required"
          :rows="field.rows || 3"
          class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-transparent"
        ></textarea>

        <select
          v-else-if="field.type === 'select'"
          :id="field.name"
          :name="field.name"
          v-model="formData[field.name]"
          :required="field.required"
          class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-transparent"
        >
          <option value="">
            {{ field.placeholder || "Select an option" }}
          </option>
          <option
            v-for="option in field.options"
            :key="option.value"
            :value="option.value"
          >
            {{ option.label }}
          </option>
        </select>

        <div v-else-if="field.type === 'radio'" class="space-y-2">
          <div
            v-for="option in field.options"
            :key="option.value"
            class="flex items-center"
          >
            <input
              :type="field.type"
              :id="`${field.name}_${option.value}`"
              :name="field.name"
              :value="option.value"
              v-model="formData[field.name]"
              class="h-4 w-4 text-blue-600 focus:ring-blue-500 border-gray-300"
            />
            <label
              :for="`${field.name}_${option.value}`"
              class="ml-2 block text-sm text-gray-700"
            >
              {{ option.label }}
            </label>
          </div>
        </div>
      </div>

      <div class="flex space-x-4">
        <button
          type="submit"
          class="flex-1 bg-blue-600 text-white py-2 px-4 rounded-md hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2 transition duration-200"
        >
          {{ submitButtonText }}
        </button>
        
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: "ReusableForm",
  props: {
    title: {
      type: String,
      required: true,
    },
    fields: {
      type: Array,
      required: true,
      validator: (fields) => {
        return fields.every((field) => field.name && field.type && field.label);
      },
    },
    submitButtonText: {
      type: String,
      default: "Submit",
    },
  },
  data() {
    return {
      formData: {},
    };
  },
  created() {
    this.initializeFormData();
  },
  methods: {
    initializeFormData() {
      this.fields.forEach((field) => {
        if (field.type === "checkbox") {
          this.formData[field.name] = false;
        } else if (field.type === "radio") {
          this.formData[field.name] = "";
        } else {
          this.formData[field.name] = "";
        }
      });
    },
    handleSubmit() {
      console.log(this.formData);
      this.$emit("form-submit", this.formData);
      alert("Form submitted successfully!");
    }
  },
};
</script>
