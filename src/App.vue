<script>
import Navigation from './components/Navigation.vue'
import Header from './components/Header.vue'
import About from './components/About.vue'
import Skills from './components/Skills.vue'
import Projects from './components/Projects.vue'
</script>

<template>
  <div class="font-sans text-gray-800">
      <Navigation />

      <Header />

      <About />

      <Skills />

      <Projects />
    <!-- Contact Section -->
    <section id="contact" class="py-20 bg-gray-50">
      <div class="container mx-auto px-6">
        <h2 class="text-4xl font-bold text-center mb-16">Get In Touch</h2>
        <div class="flex flex-col md:flex-row">
          <div class="md:w-1/2 mb-12 md:mb-0">
            <h3 class="text-2xl font-semibold mb-6">Contact Information</h3>
            <div class="space-y-6">
              <div v-for="(contact, index) in contactInfo" :key="index" class="flex items-start">
                <div class="bg-primary/10 p-3 rounded-full mr-4">
                  <component :is="contact.icon" class="h-6 w-6 text-primary" />
                </div>
                <div>
                  <h4 class="font-medium text-gray-800">{{ contact.label }}</h4>
                  <p class="text-gray-600">{{ contact.value }}</p>
                </div>
              </div>
            </div>
            <div class="mt-8">
              <h4 class="font-medium text-gray-800 mb-4">Follow Me</h4>
              <div class="flex space-x-4">
                <a v-for="(social, index) in socialLinks" :key="index" 
                   :href="social.url" 
                   class="bg-white p-3 rounded-full shadow-md hover:shadow-lg transition-shadow">
                  <component :is="social.icon" class="h-5 w-5 text-primary" />
                </a>
              </div>
            </div>
          </div>
          <div class="md:w-1/2 md:pl-12">
            <form class="bg-white p-8 rounded-lg shadow-md">
              <div class="mb-6">
                <label for="name" class="block text-gray-700 font-medium mb-2">Name</label>
                <input type="text" id="name" v-model="form.name" 
                       class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-primary focus:border-transparent" 
                       placeholder="Your name" />
              </div>
              <div class="mb-6">
                <label for="email" class="block text-gray-700 font-medium mb-2">Email</label>
                <input type="email" id="email" v-model="form.email" 
                       class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-primary focus:border-transparent" 
                       placeholder="Your email" />
              </div>
              <div class="mb-6">
                <label for="message" class="block text-gray-700 font-medium mb-2">Message</label>
                <textarea id="message" v-model="form.message" rows="5" 
                          class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-primary focus:border-transparent" 
                          placeholder="Your message"></textarea>
              </div>
              <button @click.prevent="submitForm" 
                      class="w-full bg-primary hover:bg-primary-dark text-white font-semibold py-3 px-8 rounded-lg transition-colors">
                Send Message
              </button>
            </form>
          </div>
        </div>
      </div>
    </section>

    <!-- Footer -->
    <footer class="bg-gray-800 text-white py-12">
      <div class="container mx-auto px-6">
        <div class="flex flex-col md:flex-row justify-between items-center">
          <div class="mb-6 md:mb-0">
            <a href="#" class="text-2xl font-bold">Portfolio</a>
            <p class="mt-2 text-gray-400">Creating beautiful web experiences</p>
          </div>
          <div class="flex flex-wrap justify-center gap-6">
            <a v-for="(item, index) in navItems" :key="index" 
               :href="item.href" 
               class="text-gray-400 hover:text-white transition-colors">
              {{ item.label }}
            </a>
          </div>
        </div>
        <div class="border-t border-gray-700 mt-8 pt-8 flex flex-col md:flex-row justify-between items-center">
          <p class="text-gray-400">© {{ new Date().getFullYear() }} Jane Doe. All rights reserved.</p>
          <div class="flex space-x-4 mt-4 md:mt-0">
            <a v-for="(social, index) in socialLinks" :key="index" 
               :href="social.url" 
               class="text-gray-400 hover:text-white transition-colors">
              <component :is="social.icon" class="h-5 w-5" />
            </a>
          </div>
        </div>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { 
  Menu, X, ExternalLink, Github, Mail, Phone, MapPin, 
  Linkedin, Twitter, Instagram, Code, Database, Palette, 
  Globe, Server, Cpu, Layout
} from 'lucide-vue-next';


// Contact information
const contactInfo = [
  { icon: Mail, label: 'Email', value: 'jane.doe@example.com' },
  { icon: Phone, label: 'Phone', value: '+1 (555) 123-4567' },
  { icon: MapPin, label: 'Location', value: 'San Francisco, CA' }
];

// Social links
const socialLinks = [
  { icon: Github, url: '#' },
  { icon: Linkedin, url: '#' },
  { icon: Twitter, url: '#' },
  { icon: Instagram, url: '#' }
];

// Contact form
const form = ref({
  name: '',
  email: '',
  message: ''
});

const submitForm = () => {
  console.log('Form submitted:', form.value);
  alert('Thank you for your message! I will get back to you soon.');
  form.value = { name: '', email: '', message: '' };
};
</script>

<style>
:root {
  --color-primary: #939553;
  --color-primary-dark: #a9c67f;
}

html {
  scroll-behavior: smooth;
}

.text-primary {
  color: var(--color-primary);
}

.text-primary-dark {
  color: var(--color-primary-dark);
}

.bg-primary {
  background-color: var(--color-primary);
}

.bg-primary-dark {
  background-color: var(--color-primary-dark);
}

.hover\:bg-primary:hover {
  background-color: var(--color-primary);
}

.hover\:bg-primary-dark:hover {
  background-color: var(--color-primary-dark);
}

.hover\:text-primary:hover {
  color: var(--color-primary);
}

.hover\:text-primary-dark:hover {
  color: var(--color-primary-dark);
}

.border-primary {
  border-color: var(--color-primary);
}

.bg-primary\/10 {
  background-color: rgba(99, 102, 241, 0.1);
}

.focus\:ring-primary:focus {
  --tw-ring-color: var(--color-primary);
}
</style>

