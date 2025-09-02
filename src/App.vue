<template>
  <div class="min-h-screen bg-gradient-to-b from-gray-50 to-gray-100">
    <header class="bg-white/80 backdrop-blur border-b border-gray-200 sticky top-0 z-10">
      <div class="max-w-6xl mx-auto px-4">
        <nav class="flex items-center justify-center h-14">
          
          <div class="flex items-center space-x-6 text-gray-600">
            <RouterLink to="/" class="hover:text-blue-600 transition-colors">Home</RouterLink>
            <RouterLink to="/about" class="hover:text-blue-600 transition-colors">About</RouterLink>
            <RouterLink to="/contact" class="hover:text-blue-600 transition-colors">Contact</RouterLink>
          </div>
        </nav>
      </div>
    </header>
    <main class="max-w-6xl mx-auto px-4 py-6">
      <RouterView />
    </main>
  </div>
</template>

<script>
export default {
  name: "App",
};
</script>
