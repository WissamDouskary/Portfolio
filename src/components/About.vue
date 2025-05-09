<template>
    <!-- About Section -->
<section id="about" class="py-20 bg-white">
    <div class="container mx-auto px-6">
      <h2 class="text-4xl font-bold text-center mb-16">About Me</h2>
      <div class="flex flex-col md:flex-row items-center">
        <div class="md:w-1/2 mb-12 md:mb-0">
          <img src="" alt="About Me" class="rounded-lg shadow-xl max-w-full h-auto" />
        </div>
        <div class="md:w-1/2 md:pl-12">
          <h3 class="text-2xl font-semibold mb-4">My Journey</h3>
          <p class="text-gray-600 mb-6">
            With over 5 years of experience in web development, I specialize in creating modern, responsive websites and applications. My passion lies in combining beautiful design with clean, efficient code.
          </p>
          <p class="text-gray-600 mb-8">
            I've worked with clients ranging from startups to large corporations, helping them achieve their digital goals through thoughtful design and development.
          </p>
          <div class="grid grid-cols-2 gap-4">
            <div v-for="(stat, index) in stats" :key="index" class="bg-gray-50 p-4 rounded-lg">
              <div class="text-3xl font-bold text-primary mb-2">{{ stat.value }}</div>
              <div class="text-gray-600">{{ stat.label }}</div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
const stats = [
  { value: '5+', label: 'Years Experience' },
  { value: '50+', label: 'Projects Completed' },
  { value: '30+', label: 'Happy Clients' },
  { value: '10+', label: 'Awards' }
];
</script>