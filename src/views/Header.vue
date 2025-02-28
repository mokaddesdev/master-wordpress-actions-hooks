<template>
    <header class="bg-white shadow-md py-4">
      <div class="container mx-auto flex justify-between items-center px-4">
        <!-- Logo -->
        <RouterLink to="/" class="text-2xl font-bold text-gray-800">MyShop</RouterLink>
  
        <!-- Menu -->
        <nav class="hidden md:flex space-x-6">
          <RouterLink to="/" class="text-gray-600 hover:text-blue-500">Home</RouterLink>
          <RouterLink to="/about" class="text-gray-600 hover:text-blue-500">About</RouterLink>
          <RouterLink to="/shop" class="text-gray-600 hover:text-blue-500">Shop</RouterLink>
          <RouterLink to="/contact" class="text-gray-600 hover:text-blue-500">Contact</RouterLink>
        </nav>
  
        <!-- Icons (Shopping Cart & Search) -->
        <div class="flex items-center space-x-4">
          <RouterLink to="/cart" class="text-gray-600 hover:text-blue-500">
            <i class="fas fa-shopping-cart text-xl"></i>
          </RouterLink>
          <RouterLink to="/search" class="text-gray-600 hover:text-blue-500">
            <i class="fas fa-search text-xl"></i>
          </RouterLink>
        </div>
      </div>
    </header>
  </template>
  
  <script>
  export default {
    name: "HeaderComponent",
  };
  </script>
  
  