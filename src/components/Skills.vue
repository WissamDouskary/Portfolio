<template>
    <!-- Skills Section -->
    <section id="skills" class="py-20 bg-gray-50">
        <div class="container mx-auto px-6">
            <h2 class="text-4xl font-bold text-center mb-16">My Skills</h2>
            <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-8">
                <div v-for="(skill, index) in skills" :key="index"
                    class="bg-white p-6 rounded-lg shadow-md hover:shadow-lg transition-shadow flex flex-col items-center">
                    <div class="w-16 h-16 flex items-center justify-center bg-primary/10 rounded-full mb-4">
                        <component :is="skill.icon" class="h-8 w-8 text-primary" />
                    </div>
                    <h3 class="text-xl font-semibold mb-2">{{ skill.name }}</h3>
                    <div class="w-full bg-gray-200 rounded-full h-2 mt-2">
                        <div class="bg-primary h-2 rounded-full" :style="{ width: skill.level + '%' }"></div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script>

import { 
  Menu, X, ExternalLink, Github, Mail, Phone, MapPin, 
  Linkedin, Twitter, Instagram, Code, Database, Palette, 
  Globe, Server, Cpu, Layout
} from 'lucide-vue-next';

const skills = [
    { name: 'Vue.js', level: 95, icon: Code },
    { name: 'JavaScript', level: 90, icon: Code },
    { name: 'HTML/CSS', level: 95, icon: Layout },
    { name: 'Tailwind CSS', level: 90, icon: Palette },
    { name: 'UI/UX Design', level: 85, icon: Palette },
    { name: 'Node.js', level: 80, icon: Server },
    { name: 'MongoDB', level: 75, icon: Database },
    { name: 'Responsive Design', level: 95, icon: Globe }
];

</script>