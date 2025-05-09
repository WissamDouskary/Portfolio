<template>
        <!-- Projects Section -->
    <section id="projects" class="py-20 bg-white">
      <div class="container mx-auto px-6">
        <h2 class="text-4xl font-bold text-center mb-16">My Projects</h2>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          <div v-for="(project, index) in projects" :key="index" 
               class="bg-white rounded-lg overflow-hidden shadow-md hover:shadow-xl transition-shadow">
            <div class="relative overflow-hidden" style="height: 200px;">
              <img :src="project.image" :alt="project.title" class="w-full h-full object-cover transition-transform duration-500 hover:scale-110" />
            </div>
            <div class="p-6">
              <h3 class="text-xl font-semibold mb-2">{{ project.title }}</h3>
              <p class="text-gray-600 mb-4">{{ project.description }}</p>
              <div class="flex flex-wrap gap-2 mb-4">
                <span v-for="(tech, techIndex) in project.technologies" :key="techIndex" 
                      class="bg-gray-100 text-gray-800 text-xs font-medium px-2.5 py-0.5 rounded">
                  {{ tech }}
                </span>
              </div>
              <div class="flex space-x-3">
                <a :href="project.liveUrl" class="text-primary hover:text-primary-dark font-medium flex items-center">
                  <ExternalLink class="h-4 w-4 mr-1" /> Live
                </a>
                <a :href="project.codeUrl" class="text-primary hover:text-primary-dark font-medium flex items-center">
                  <Github class="h-4 w-4 mr-1" /> Code
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
</template>

<script>
const projects = [
  {
    title: 'E-commerce Website',
    description: 'A fully responsive e-commerce platform with cart functionality and payment integration.',
    image: '',
    technologies: ['Vue.js', 'Vuex', 'Tailwind CSS', 'Node.js'],
    liveUrl: '#',
    codeUrl: '#'
  },
  {
    title: 'Task Management App',
    description: 'A drag-and-drop task management application with user authentication.',
    image: '',
    technologies: ['Vue.js', 'Firebase', 'Tailwind CSS'],
    liveUrl: '#',
    codeUrl: '#'
  },
  {
    title: 'Portfolio Website',
    description: 'A modern portfolio website showcasing projects and skills.',
    image: '',
    technologies: ['Vue.js', 'Tailwind CSS', 'GSAP'],
    liveUrl: '#',
    codeUrl: '#'
  },
  {
    title: 'Weather Dashboard',
    description: 'A weather application showing forecasts and historical data.',
    image: '',
    technologies: ['Vue.js', 'Chart.js', 'Weather API'],
    liveUrl: '#',
    codeUrl: '#'
  },
  {
    title: 'Recipe Finder',
    description: 'An application to search and save recipes with filtering options.',
    image: '',
    technologies: ['Vue.js', 'Vuex', 'Food API'],
    liveUrl: '#',
    codeUrl: '#'
  },
  {
    title: 'Fitness Tracker',
    description: 'A fitness tracking application with progress visualization.',
    image: '',
    technologies: ['Vue.js', 'Chart.js', 'LocalStorage'],
    liveUrl: '#',
    codeUrl: '#'
  }
];
</script>