<!-- The exported code uses Tailwind CSS. Install Tailwind CSS in your dev environment to ensure all styles work. -->

<template>
  <div class="min-h-screen flex items-center justify-center bg-gradient-to-br from-gray-900 to-black overflow-hidden relative">
    <!-- Background particles effect -->
    <div class="absolute inset-0 z-0">
      <div id="particles-container" class="w-full h-full"></div>
    </div>
    
    <!-- Main container -->
    <div class="container mx-auto px-4 z-10">
      <div class="flex flex-col lg:flex-row bg-black/30 backdrop-blur-md rounded-xl overflow-hidden shadow-2xl max-w-6xl mx-auto border border-purple-500/20">
        
        <!-- Left panel -->
        <div class="w-full lg:w-1/2 p-8 lg:p-12 relative overflow-hidden">
          <div class="relative z-10">
            <!-- Company logo -->
            <div class="mb-12">
              <h1 class="text-4xl font-bold text-transparent bg-clip-text bg-gradient-to-r from-blue-400 to-purple-600 inline-block">
                <span class="text-white">@</span>Reality
              </h1>
              <div class="h-1 w-20 bg-gradient-to-r from-blue-500 to-purple-600 mt-2"></div>
            </div>
            
            <!-- Tagline -->
            <div class="mb-8">
              <h2 class="text-3xl lg:text-4xl font-light text-white leading-tight mb-4">Shape the future<br />beyond imagination</h2>
              <p class="text-gray-400 mb-8">Pioneering the next generation of immersive reality experiences since 2025.</p>
            </div>
            
            <!-- Features -->
            <div class="space-y-4 mt-12">
              <div class="flex items-center">
                <div class="w-10 h-10 rounded-full bg-blue-500/10 flex items-center justify-center mr-4">
                  <i class="fas fa-vr-cardboard text-blue-400"></i>
                </div>
                <p class="text-gray-300">Advanced virtual reality environments</p>
              </div>
              <div class="flex items-center">
                <div class="w-10 h-10 rounded-full bg-purple-500/10 flex items-center justify-center mr-4">
                  <i class="fas fa-brain text-purple-400"></i>
                </div>
                <p class="text-gray-300">Neural interface technology</p>
              </div>
              <div class="flex items-center">
                <div class="w-10 h-10 rounded-full bg-indigo-500/10 flex items-center justify-center mr-4">
                  <i class="fas fa-project-diagram text-indigo-400"></i>
                </div>
                <p class="text-gray-300">Quantum computing integration</p>
              </div>
            </div>
          </div>
          
          <!-- Background image -->
          <div class="absolute inset-0 z-0 opacity-20">
            <img 
              src="https://readdy.ai/api/search-image?query=futuristic%20abstract%20technology%20background%20with%20glowing%20blue%20and%20purple%20neon%20geometric%20shapes%2C%20digital%20particles%20floating%20in%20dark%20space%2C%20cyberpunk%20aesthetic%2C%20high%20tech%2C%20ultra%20modern%2C%20minimalist%20design%20with%20depth&width=800&height=1000&seq=1&orientation=portrait" 
              alt="Futuristic background" 
              class="w-full h-full object-cover object-top"
            />
          </div>
        </div>
        
        <!-- Right panel - Sign in form -->
        <div class="w-full lg:w-1/2 p-8 lg:p-12 bg-black/50 backdrop-blur-md">
          <div class="max-w-md mx-auto">
            <h2 class="text-3xl font-bold text-white mb-8">Sign In</h2>
            
            <form @submit.prevent="handleSubmit">
              <!-- Email input -->
              <div class="mb-6">
                <label for="email" class="block text-gray-400 text-sm mb-2">Email</label>
                <div class="relative">
                  <input 
                    type="email" 
                    id="email" 
                    v-model="email" 
                    class="w-full bg-gray-900/80 border-none !rounded-button text-white px-4 py-3 focus:ring-2 focus:ring-blue-500 transition-all"
                    :class="{'ring-2 ring-red-500': emailError}"
                    placeholder="your@email.com"
                    required
                  />
                  <div class="absolute inset-y-0 left-3 flex items-center pointer-events-none">
                    <i class="fas fa-envelope text-gray-500 text-sm"></i>
                  </div>
                  <div class="absolute inset-y-0 right-3 flex items-center" v-if="email">
                    <i class="fas fa-check-circle text-green-500" v-if="isValidEmail"></i>
                    <i class="fas fa-times-circle text-red-500" v-else></i>
                  </div>
                </div>
                <p class="text-red-500 text-xs mt-1" v-if="emailError">{{ emailError }}</p>
              </div>
              
              <!-- Password input -->
              <div class="mb-6">
                <label for="password" class="block text-gray-400 text-sm mb-2">Password</label>
                <div class="relative">
                  <input 
                    :type="showPassword ? 'text' : 'password'" 
                    id="password" 
                    v-model="password"
                    class="w-full bg-gray-900/80 border-none !rounded-button text-white px-4 py-3 focus:ring-2 focus:ring-blue-500 transition-all"
                    :class="{'ring-2 ring-red-500': passwordError}"
                    placeholder="••••••••"
                    required
                  />
                  <div class="absolute inset-y-0 left-3 flex items-center pointer-events-none">
                    <i class="fas fa-lock text-gray-500 text-sm"></i>
                  </div>
                  <div class="absolute inset-y-0 right-3 flex items-center">
                    <button 
                      type="button" 
                      @click="showPassword = !showPassword"
                      class="text-gray-400 hover:text-white focus:outline-none cursor-pointer whitespace-nowrap !rounded-button"
                    >
                      <i :class="showPassword ? 'fas fa-eye-slash' : 'fas fa-eye'"></i>
                    </button>
                  </div>
                </div>
                <p class="text-red-500 text-xs mt-1" v-if="passwordError">{{ passwordError }}</p>
              </div>
              
              <!-- Remember me checkbox -->
              <div class="flex items-center justify-between mb-6">
                <div class="flex items-center">
                  <input 
                    type="checkbox" 
                    id="remember" 
                    v-model="rememberMe"
                    class="h-4 w-4 bg-gray-900 border-none rounded text-blue-500 focus:ring-blue-500 focus:ring-offset-gray-900"
                  />
                  <label for="remember" class="ml-2 text-sm text-gray-400 cursor-pointer">Remember me</label>
                </div>
                <a href="#" class="text-sm text-blue-400 hover:text-blue-300 transition-colors">Forgot password?</a>
              </div>
              
              <!-- Sign in button -->
              <button 
                type="submit" 
                class="w-full bg-gradient-to-r from-blue-600 to-purple-600 hover:from-blue-500 hover:to-purple-500 text-white font-medium py-3 px-4 !rounded-button transition-all shadow-lg shadow-purple-500/20 cursor-pointer whitespace-nowrap"
                :class="{'opacity-75': isLoading}"
                :disabled="isLoading"
              >
                <span v-if="!isLoading">Sign In</span>
                <span v-else class="flex items-center justify-center">
                  <i class="fas fa-circle-notch fa-spin mr-2"></i> Signing in...
                </span>
              </button>
              
              <!-- Social sign in -->
              <div class="mt-8">
                <div class="flex items-center justify-between mb-4">
                  <div class="w-full h-px bg-gray-800"></div>
                  <span class="px-4 text-sm text-gray-500">or continue with</span>
                  <div class="w-full h-px bg-gray-800"></div>
                </div>
                
                <div class="grid grid-cols-3 gap-3">
                  <button 
                    type="button" 
                    class="flex justify-center items-center py-2.5 px-4 bg-gray-900 hover:bg-gray-800 !rounded-button border border-gray-800 transition-colors cursor-pointer whitespace-nowrap"
                  >
                    <i class="fab fa-google text-white"></i>
                  </button>
                  <button 
                    type="button" 
                    class="flex justify-center items-center py-2.5 px-4 bg-gray-900 hover:bg-gray-800 !rounded-button border border-gray-800 transition-colors cursor-pointer whitespace-nowrap"
                  >
                    <i class="fab fa-apple text-white"></i>
                  </button>
                  <button 
                    type="button" 
                    class="flex justify-center items-center py-2.5 px-4 bg-gray-900 hover:bg-gray-800 !rounded-button border border-gray-800 transition-colors cursor-pointer whitespace-nowrap"
                  >
                    <i class="fab fa-microsoft text-white"></i>
                  </button>
                </div>
              </div>
              
              <!-- Sign up link -->
              <div class="mt-8 text-center">
                <p class="text-gray-400 text-sm">
                  Don't have an account? 
                  <a href="#" class="text-blue-400 hover:text-blue-300 transition-colors">Create account</a>
                </p>
              </div>
            </form>
          </div>
        </div>
      </div>
      
      <!-- Current date display -->
      <div class="text-center mt-6 text-gray-500 text-sm">
        <p>{{ currentDate }}</p>
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { ref, computed, onMounted } from 'vue';

// Form state
const email = ref('');
const password = ref('');
const rememberMe = ref(false);
const showPassword = ref(false);
const isLoading = ref(false);
const emailError = ref('');
const passwordError = ref('');

// Computed properties
const isValidEmail = computed(() => {
  const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
  return emailRegex.test(email.value);
});

const currentDate = computed(() => {
  const date = new Date();
  return date.toLocaleDateString('en-US', { 
    weekday: 'long',
    year: 'numeric', 
    month: 'long', 
    day: 'numeric' 
  });
});

// Methods
const handleSubmit = () => {
  // Reset errors
  emailError.value = '';
  passwordError.value = '';
  
  // Validate email
  if (!email.value) {
    emailError.value = 'Email is required';
    return;
  }
  
  if (!isValidEmail.value) {
    emailError.value = 'Please enter a valid email address';
    return;
  }
  
  // Validate password
  if (!password.value) {
    passwordError.value = 'Password is required';
    return;
  }
  
  if (password.value.length < 8) {
    passwordError.value = 'Password must be at least 8 characters';
    return;
  }
  
  // Submit form
  isLoading.value = true;
  
  // Simulate API call
  setTimeout(() => {
    isLoading.value = false;
    // Here you would normally redirect or update UI based on successful login
    console.log('Form submitted', { email: email.value, password: password.value, rememberMe: rememberMe.value });
  }, 2000);
};

// Initialize particles.js
onMounted(() => {
  if (typeof window !== 'undefined') {
    // Create and append script element for particles.js
    const script = document.createElement('script');
    script.src = 'https://cdn.jsdelivr.net/particles.js/2.0.0/particles.min.js';
    script.onload = () => {
      // @ts-ignore
      if (window.particlesJS) {
        // @ts-ignore
        window.particlesJS('particles-container', {
          particles: {
            number: {
              value: 80,
              density: {
                enable: true,
                value_area: 800
              }
            },
            color: {
              value: '#ffffff'
            },
            shape: {
              type: 'circle',
              stroke: {
                width: 0,
                color: '#000000'
              },
            },
            opacity: {
              value: 0.5,
              random: false,
              anim: {
                enable: false,
                speed: 1,
                opacity_min: 0.1,
                sync: false
              }
            },
            size: {
              value: 3,
              random: true,
              anim: {
                enable: false,
                speed: 40,
                size_min: 0.1,
                sync: false
              }
            },
            line_linked: {
              enable: true,
              distance: 150,
              color: '#6366f1',
              opacity: 0.4,
              width: 1
            },
            move: {
              enable: true,
              speed: 2,
              direction: 'none',
              random: false,
              straight: false,
              out_mode: 'out',
              bounce: false,
              attract: {
                enable: false,
                rotateX: 600,
                rotateY: 1200
              }
            }
          },
          interactivity: {
            detect_on: 'canvas',
            events: {
              onhover: {
                enable: true,
                mode: 'grab'
              },
              onclick: {
                enable: true,
                mode: 'push'
              },
              resize: true
            },
            modes: {
              grab: {
                distance: 140,
                line_linked: {
                  opacity: 1
                }
              },
              bubble: {
                distance: 400,
                size: 40,
                duration: 2,
                opacity: 8,
                speed: 3
              },
              repulse: {
                distance: 200,
                duration: 0.4
              },
              push: {
                particles_nb: 4
              },
              remove: {
                particles_nb: 2
              }
            }
          },
          retina_detect: true
        });
      }
    };
    document.head.appendChild(script);
  }
});
</script>

<style scoped>
/* Custom styles for inputs */
input:focus {
  outline: none;
  box-shadow: 0 0 0 2px rgba(99, 102, 241, 0.5), 0 0 15px rgba(99, 102, 241, 0.3);
}

/* Remove number input arrows */
input[type=number]::-webkit-inner-spin-button, 
input[type=number]::-webkit-outer-spin-button { 
  -webkit-appearance: none; 
  margin: 0; 
}

input[type=number] {
  -moz-appearance: textfield;
}

/* Custom checkbox styling */
input[type="checkbox"] {
  position: relative;
  cursor: pointer;
}

input[type="checkbox"]:checked {
  background-color: #6366f1;
  border-color: #6366f1;
}

/* Particle container */
#particles-container {
  position: absolute;
  width: 100%;
  height: 100%;
  background-color: transparent;
}
</style>
