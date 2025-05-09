<template>
  <header class="fixed w-full z-50">
    <!-- Desktop Navigation -->
    <nav 
      class="bg-white/90 backdrop-blur-md border-b border-gray-100 shadow-sm transition-all duration-300"
      :class="{ 'shadow-md': scrolled }"
    >
      <div class="container mx-auto px-6 py-4 flex justify-between items-center">
        <!-- Logo -->
        <a href="#" class="text-2xl font-bold text-primary relative group">
          WD
          <span class="absolute -bottom-1 left-0 w-0 h-0.5 bg-primary transition-all duration-300 group-hover:w-full"></span>
        </a>
        
        <!-- Desktop Menu -->
        <div class="hidden md:flex items-center space-x-1">
          <a 
            v-for="(item, index) in navItems" 
            :key="index" 
            :href="item.href"
            class="relative px-4 py-2 rounded-md text-gray-600 font-medium transition-all duration-200 hover:text-primary group"
            :class="{ 'text-primary': activeSection === item.href.substring(1) }"
          >
            {{ item.label }}
            <span 
              class="absolute bottom-0 left-1/2 -translate-x-1/2 w-0 h-0.5 bg-primary transition-all duration-300 group-hover:w-4/5"
              :class="{ 'w-4/5': activeSection === item.href.substring(1) }"
            ></span>
          </a>
        </div>
        
        <!-- Mobile Menu Button -->
        <button 
          @click="toggleMobileMenu" 
          class="md:hidden relative z-50 p-2 rounded-md hover:bg-gray-100 transition-colors"
          aria-label="Toggle menu"
        >
          <div class="w-6 flex flex-col justify-center items-center">
            <span 
              class="block w-5 h-0.5 bg-gray-600 transition-all duration-300"
              :class="{ 'rotate-45 translate-y-1.5': mobileMenuOpen }"
            ></span>
            <span 
              class="block w-5 h-0.5 bg-gray-600 my-1 transition-all duration-300"
              :class="{ 'opacity-0': mobileMenuOpen }"
            ></span>
            <span 
              class="block w-5 h-0.5 bg-gray-600 transition-all duration-300"
              :class="{ '-rotate-45 -translate-y-1.5': mobileMenuOpen }"
            ></span>
          </div>
        </button>
      </div>
    </nav>
    
    <!-- Mobile Menu Overlay -->
    <div 
      v-if="mobileMenuOpen" 
      class="fixed inset-0 bg-black/50 z-40 md:hidden"
      @click="mobileMenuOpen = false"
    ></div>
    
    <!-- Mobile Menu -->
    <div 
      class="fixed top-0 right-0 h-full w-64 bg-white z-40 shadow-xl transform transition-transform duration-300 ease-in-out md:hidden"
      :class="{ 'translate-x-0': mobileMenuOpen, 'translate-x-full': !mobileMenuOpen }"
    >
      <div class="flex flex-col h-full pt-20 pb-6 px-6">
        <div class="flex-1 flex flex-col space-y-2">
          <a 
            v-for="(item, index) in navItems" 
            :key="index" 
            :href="item.href"
            @click="closeMobileMenu" 
            class="py-3 px-4 rounded-md text-gray-600 font-medium transition-all duration-200 hover:bg-gray-50 hover:text-primary flex items-center"
            :class="{ 'bg-gray-50 text-primary': activeSection === item.href.substring(1) }"
          >
            {{ item.label }}
          </a>
        </div>
      </div>
    </div>
  </header>
</template>

<script setup>
import { RatIcon } from 'lucide-vue-next';
import { ref, onMounted, onUnmounted } from 'vue';

const mobileMenuOpen = ref(false);
const scrolled = ref(false);
const activeSection = ref('home');

const navItems = [
  { label: 'Home', href: '#home' },
  { label: 'About', href: '#about' },
  { label: 'Skills', href: '#skills' },
  { label: 'Projects', href: '#projects' },
  { label: 'Contact', href: '#contact' }
];

const toggleMobileMenu = () => {
  mobileMenuOpen.value = !mobileMenuOpen.value;
  if (mobileMenuOpen.value) {
    document.body.style.overflow = 'hidden';
  } else {
    document.body.style.overflow = '';
  }
};

const closeMobileMenu = () => {
  mobileMenuOpen.value = false;
  document.body.style.overflow = '';
};

const handleScroll = () => {
  scrolled.value = window.scrollY > 20;
  
  const sections = navItems.map(item => item.href.substring(1));
  
  for (const section of sections) {
    const element = document.getElementById(section);
    if (element) {
      const rect = element.getBoundingClientRect();
      
      if (rect.top <= 100 && rect.bottom >= 100) {
        activeSection.value = section;
        break;
      }
    }
  }
};

onMounted(() => {
  window.addEventListener('scroll', handleScroll);
  handleScroll();
});

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll);
});
</script>