<template>
  <div>
    <!-- Hero Section with Enhanced Design -->
    <div class="hero-section py-20 bg-gradient-to-br from-white to-yellow-50 relative overflow-hidden">
      <!-- Decorative background elements -->
      <div class="absolute top-0 left-0 w-full h-full overflow-hidden pointer-events-none">
        <div class="decorative-circle top-10 left-10 w-24 h-24 animate-pulse-slow"></div>
        <div class="decorative-circle bottom-20 right-10 w-32 h-32 animate-pulse-slow" style="animation-delay: 0.5s;"></div>
        <div class="decorative-circle top-1/2 right-1/4 w-16 h-16 animate-pulse-slow" style="animation-delay: 1s;"></div>
        <div class="decorative-line top-1/3 left-0"></div>
        <div class="decorative-line bottom-1/3 right-0"></div>
      </div>
      
      <div class="container mx-auto px-4 relative z-10">
        <div class="flex flex-col md:flex-row items-center">
          <div class="md:w-1/2 mb-10 md:mb-0 md:pr-1 transform transition-all duration-700" :class="{'translate-y-0 opacity-100': isVisible, 'translate-y-10 opacity-0': !isVisible}">
            <h1 class="text-4xl md:text-5xl font-bold mb-6 text-yellow-600 animate-fade-in-down">
              Professional Nail Artistry
            </h1>
            
            <!-- Enhanced Ampersand section -->
            <div class="flex justify-center mb-6 animate-fade-in-up relative">
              <div class="absolute inset-0 bg-yellow-100 rounded-full filter blur-xl opacity-30 animate-pulse"></div>
              <v-img src="../assets/ampersand.png" class="w-32 h-auto hover:scale-110 transition-transform duration-500 relative z-10"></v-img>
            </div>
            
            <p class="text-lg mb-8 text-gray-600 animate-fade-in-up animation-delay-200">
              Experience luxury nail services in the comfort of your home. Our expert technicians bring the salon to you!
            </p>
            <div class="flex flex-wrap animate-fade-in-up animation-delay-400">
              <router-link
                to="/appointments"
                class="btn-primary mr-4 mb-4 inline-flex items-center group"
              >
                <svg class="w-5 h-5 mr-2 group-hover:animate-pulse" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z"></path>
                </svg>
                Book Now
              </router-link>
              <router-link
                to="/services"
                class="border border-yellow-600 text-yellow-600 px-6 py-3 rounded-full font-medium hover:bg-yellow-50 transition-all duration-300 hover:shadow-md transform hover:-translate-y-1 mb-4 inline-flex items-center group"
              >
                <svg class="w-5 h-5 mr-2 group-hover:animate-pulse" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19.428 15.428a2 2 0 00-1.022-.547l-2.387-.477a6 6 0 00-3.86.517l-.318.158a6 6 0 01-3.86.517L6.05 15.21a2 2 0 00-1.806.547M8 4h8l-1 1v5.172a2 2 0 00.586 1.414l5 5c1.26 1.26.367 3.414-1.415 3.414H4.828c-1.782 0-2.674-2.154-1.414-3.414l5-5A2 2 0 009 10.172V5L8 4z"></path>
                </svg>
                Our Services
              </router-link>
            </div>
          </div>
          
          <!-- Enhanced Right side - Sandra's image -->
          <div class="md:w-1/2 text-center transform transition-all duration-1000" :class="{'translate-x-0 opacity-100': isVisible, 'translate-x-10 opacity-0': !isVisible}">
            <div class="relative inline-block">
              <div class="absolute -inset-4 bg-gradient-to-r from-yellow-400 to-yellow-200 rounded-2xl blur-xl opacity-30 animate-pulse"></div>
              <img
                src="../assets/sandra.png"
                alt="Sandra Kate Gudez - Nail Technician"
                class="rounded-xl shadow-lg mx-auto transform transition-all duration-700 hover:scale-105 hover:shadow-2xl max-w-full h-auto animate-float relative z-10"
              />
              <!-- Enhanced decorative element -->
              <div class="absolute -bottom-4 -right-4 bg-gradient-to-r from-yellow-500 to-yellow-300 text-white rounded-lg p-3 shadow-lg transform rotate-6 hover:rotate-3 transition-transform duration-500 animate-bounce-slow">
                <p class="text-sm font-bold">3+ Years Experience</p>
              </div>
            </div>
            <div class="mt-6 animate-fade-in animation-delay-600">
              <h2 class="text-2xl font-bold text-yellow-600 cursive">SANDRA KATE GUDEZ</h2>
              <p class="text-gray-600 italic">Master Nail Technician & Owner</p>
              <div class="flex justify-center mt-3 space-x-4">
                <a href="#" class="text-yellow-600 hover:text-yellow-700 transform hover:scale-125 transition-all duration-300">
                  <svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true">
                    <path fill-rule="evenodd" d="M12.315 2c2.43 0 2.784.013 3.808.06 1.064.049 1.791.218 2.427.465a4.902 4.902 0 011.772 1.153 4.902 4.902 0 011.153 1.772c.247.636.416 1.363.465 2.427.048 1.067.06 1.407.06 4.123v.08c0 2.643-.012 2.987-.06 4.043-.049 1.064-.218 1.791-.465 2.427a4.902 4.902 0 01-1.153 1.772 4.902 4.902 0 01-1.772 1.153c-.636.247-1.363.416-2.427.465-1.067.048-1.407.06-4.123.06h-.08c-2.643 0-2.987-.012-4.043-.06-1.064-.049-1.791-.218-2.427-.465a4.902 4.902 0 01-1.772-1.153 4.902 4.902 0 01-1.153-1.772c-.247-.636-.416-1.363-.465-2.427-.047-1.024-.06-1.379-.06-3.808v-.63c0-2.43.013-2.784.06-3.808.049-1.064.218-1.791.465-2.427a4.902 4.902 0 011.153-1.772A4.902 4.902 0 015.45 2.525c.636-.247 1.363-.416 2.427-.465C8.901 2.013 9.256 2 11.685 2h.63zm-.081 1.802h-.468c-2.456 0-2.784.011-3.807.058-.975.045-1.504.207-1.857.344-.467.182-.8.398-1.15.748-.35.35-.566.683-.748 1.15-.137.353-.3.882-.344 1.857-.047 1.023-.058 1.351-.058 3.807v.468c0 2.456.011 2.784.058 3.807.045.975.207 1.504.344 1.857.182.466.399.8.748 1.15.35.35.683.566 1.15.748.353.137.882.3 1.857.344 1.054.048 1.37.058 4.041.058h.08c2.597 0 2.917-.01 3.96-.058.976-.045 1.505-.207 1.858-.344.466-.182.8-.398 1.15-.748.35-.35.566-.683.748-1.15.137-.353.3-.882.344-1.857.048-1.055.058-1.37.058-4.041v-.08c0-2.597-.01-2.917-.058-3.96-.045-.976-.207-1.505-.344-1.858a3.097 3.097 0 00-.748-1.15 3.098 3.098 0 00-1.15-.748c-.353-.137-.882-.3-1.857-.344-1.023-.047-1.351-.058-3.807-.058zM12 6.865a5.135 5.135 0 110 10.27 5.135 5.135 0 010-10.27zm0 1.802a3.333 3.333 0 100 6.666 3.333 3.333 0 000-6.666zm5.338-3.205a1.2 1.2 0 110 2.4 1.2 1.2 0 010-2.4z" clip-rule="evenodd" />
                  </svg>
                </a>
                <a href="#" class="text-yellow-600 hover:text-yellow-700 transform hover:scale-125 transition-all duration-300">
                  <svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true">
                    <path fill-rule="evenodd" d="M22 12c0-5.523-4.477-10-10-10S2 6.477 2 12c0 4.991 3.657 9.128 8.438 9.878v-6.987h-2.54V12h2.54V9.797c0-2.506 1.492-3.89 3.777-3.89 1.094 0 2.238.195 2.238.195v2.46h-1.26c-1.243 0-1.63.771-1.63 1.562V12h2.773l-.443 2.89h-2.33v6.988C18.343 21.128 22 16.991 22 12z" clip-rule="evenodd" />
                  </svg>
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>
      
      <!-- Gold curve at bottom of hero -->
      <div class="gold-curve"></div>
    </div>

    <!-- Enhanced About Section -->
    <div class="py-16 bg-white relative">
      <div class="container mx-auto px-4">
        <div class="max-w-3xl mx-auto text-center">
          <h2 class="text-3xl font-bold mb-4 text-yellow-600 serif gold-accent animate-fade-in">Meet Your Nail Artist</h2>
          <div class="w-24 h-1 bg-yellow-500 mx-auto mb-6 animate-scale-in"></div>
          <p class="text-gray-600 mb-10 animate-fade-in animation-delay-200 text-lg">
            With over a decade of experience in the nail industry, Sandra Kate Gudez brings passion, creativity, and precision to every client. Her dedication to the craft and attention to detail ensures that each client leaves with nails that not only look beautiful but are also healthy and well-cared for.
          </p>
          <div class="grid grid-cols-1 md:grid-cols-3 gap-8 mt-12">
            <div class="girlie-card p-8 animate-fade-in-up animation-delay-300">
              <div class="service-icon mx-auto mb-6">
                <svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m5.618-4.016A11.955 11.955 0 0112 2.944a11.955 11.955 0 01-8.618 3.04A12.02 12.02 0 003 9c0 5.591 3.824 10.29 9 11.622 5.176-1.332 9-6.03 9-11.622 0-1.042-.133-2.052-.382-3.016z"></path>
                </svg>
              </div>
              <h3 class="text-xl font-bold mb-3">Certified Professional</h3>
              <p class="text-gray-600">Fully licensed and certified in all nail techniques</p>
            </div>
            <div class="girlie-card p-8 animate-fade-in-up animation-delay-500">
              <div class="service-icon mx-auto mb-6">
                <svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M7 8h10M7 12h4m1 8l-4-4H5a2 2 0 01-2-2V6a2 2 0 012-2h14a2 2 0 012 2v8a2 2 0 01-2 2h-3l-4 4z"></path>
                </svg>
              </div>
              <h3 class="text-xl font-bold mb-3">Personalized Service</h3>
              <p class="text-gray-600">Custom designs tailored to your unique style</p>
            </div>
            <div class="girlie-card p-8 animate-fade-in-up animation-delay-700">
              <div class="service-icon mx-auto mb-6">
                <svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z"></path>
                </svg>
              </div>
              <h3 class="text-xl font-bold mb-3">Latest Trends</h3>
              <p class="text-gray-600">Always up-to-date with the latest nail art trends</p>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Enhanced Home Service Section -->
    <div class="py-16 bg-yellow-50 relative">
      <div class="gold-curve" style="top: -1px; bottom: auto; transform: rotate(180deg);"></div>
      
      <div class="container mx-auto px-4 relative z-10">
        <div class="text-center mb-12">
          <h2 class="text-3xl font-bold mb-2 text-yellow-600 serif gold-accent">Home Service</h2>
          <p class="text-gray-600 max-w-2xl mx-auto text-lg">
            Enjoy our professional nail services in the comfort of your own home. We bring everything needed for a perfect manicure or pedicure experience.
          </p>
        </div>
        
        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
          <div class="bg-white rounded-xl shadow-md p-8 hover:shadow-xl transition-all duration-500 transform hover:-translate-y-2 animate-fade-in-up animation-delay-300">
            <div class="service-icon mx-auto mb-6">
              <svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"></path>
              </svg>
            </div>
            <h3 class="text-xl font-bold mb-3 text-center">Transportation Included</h3>
            <p class="text-gray-600 text-center">
              Our technicians travel to your location with all necessary equipment and products.
            </p>
          </div>
          
          <div class="bg-white rounded-xl shadow-md p-8 hover:shadow-xl transition-all duration-500 transform hover:-translate-y-2 animate-fade-in-up animation-delay-500">
            <div class="service-icon mx-auto mb-6">
              <svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 12l2-2m0 0l7-7 7 7M5 10v10a1 1 0 001 1h3m10-11l2 2m-2-2v10a1 1 0 01-1 1h-3m-6 0a1 1 0 001-1v-4a1 1 0 011-1h2a1 1 0 011 1v4a1 1 0 001 1m-6 0h6"></path>
              </svg>
            </div>
            <h3 class="text-xl font-bold mb-3 text-center">Home Service Fee</h3>
            <p class="text-gray-600 text-center">
              A small home service fee is added to cover travel expenses and setup time.
            </p>
          </div>
          
          <div class="bg-white rounded-xl shadow-md p-8 hover:shadow-xl transition-all duration-500 transform hover:-translate-y-2 animate-fade-in-up animation-delay-700">
            <div class="service-icon mx-auto mb-6">
              <svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z"></path>
              </svg>
            </div>
            <h3 class="text-xl font-bold mb-3 text-center">Flexible Scheduling</h3>
            <p class="text-gray-600 text-center">
              Book appointments at your convenience, including evenings and weekends.
            </p>
          </div>
        </div>
      </div>
      
      <div class="gold-curve"></div>
    </div>

    <!-- Enhanced Services Preview -->
    <div class="py-16 bg-white relative">
      <div class="container mx-auto px-4">
        <div class="text-center mb-12">
          <h2 class="text-3xl font-bold mb-2 text-yellow-600 serif gold-accent">Our Services</h2>
          <p class="text-gray-600 max-w-2xl mx-auto text-lg">
            We offer a wide range of nail services to suit your style and preferences.
          </p>
        </div>
        
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
          <div v-for="(service, index) in services" :key="index" class="girlie-card p-8 text-center animate-fade-in-up" :style="`animation-delay: ${300 + index * 100}ms`">
            <div class="service-icon mx-auto mb-6">
              <svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 3v4M3 5h4M6 17v4m-2-2h4m5-16l2.286 6.857L21 12l-5.714 2.143L13 21l-2.286-6.857L5 12l5.714-2.143L13 3z"></path>
              </svg>
            </div>
            <h3 class="text-lg font-bold mb-2">{{ service.name }}</h3>
            <p class="text-gray-600 mb-4">{{ service.description }}</p>
            <router-link
              to="/services"
              class="text-yellow-600 font-medium hover:text-yellow-700 inline-flex items-center group"
            >
              Learn More
              <svg class="w-4 h-4 ml-1 group-hover:translate-x-1 transition-transform duration-300" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"></path>
              </svg>
            </router-link>
          </div>
        </div>
      </div>
    </div>

    <!-- Enhanced Popular Designs -->
    <div class="py-16 bg-yellow-50 relative">
      <div class="gold-curve" style="top: -1px; bottom: auto; transform: rotate(180deg);"></div>
      
      <div class="container mx-auto px-4 relative z-10">
        <div class="text-center mb-12">
          <h2 class="text-3xl font-bold mb-2 text-yellow-600 serif gold-accent">Popular Nail Designs</h2>
          <p class="text-gray-600 max-w-2xl mx-auto text-lg">
            Explore our most requested nail art designs and trends.
          </p>
        </div>
        
        <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-8">
          <div v-for="(design, index) in popularDesigns" :key="index" class="gallery-item animate-fade-in-up" :style="`animation-delay: ${300 + index * 100}ms`">
            <div class="h-64 bg-gradient-to-r from-yellow-100 to-yellow-200 flex items-center justify-center relative overflow-hidden group">
               <v-img
              :src="design.link"
              alt="design.name"
              class="design-image"
              :title="design.name"
              cover
            ></v-img>
              <div class="absolute inset-0 bg-gradient-to-r from-yellow-200 to-yellow-300 opacity-0 group-hover:opacity-100 transition-opacity duration-500 transform scale-110 group-hover:scale-100"></div>
            </div>
            <div class="p-6 bg-white">
              <h3 class="font-bold mb-1">{{ design.name }}</h3>
              <p class="text-gray-600 text-sm">{{ design.description }}</p>
              <div class="mt-3 flex justify-between items-center">
                <router-link to="/gallery" class="text-sm text-yellow-600 hover:text-yellow-700 group inline-flex items-center">
                  View Gallery
                  <svg class="w-4 h-4 ml-1 group-hover:translate-x-1 transition-transform duration-300" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"></path>
                  </svg>
                </router-link>
              </div>
            </div>
          </div>
        </div>
        
        <div class="text-center mt-10 animate-fade-in animation-delay-800">
          <router-link to="/gallery" class="btn-primary inline-flex items-center group">
            View All Designs
            <svg class="w-5 h-5 ml-2 group-hover:translate-x-1 transition-transform duration-300" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14 5l7 7m0 0l-7 7m7-7H3"></path>
            </svg>
          </router-link>
        </div>
      </div>
      
      <div class="gold-curve"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Home',
  data() {
    return {
      isVisible: false,
      services: [
        {
          name: 'Gel Nails',
          description: 'Long-lasting, glossy finish that cures under UV light.'
        },
        {
          name: 'Nail Extensions',
          description: 'Add length and strength to your natural nails.'
        },
        {
          name: 'Fill-in / Floaters',
          description: 'Maintain your extensions with a fill-in service.'
        },
        {
          name: 'Gel Polish Add-on',
          description: 'Upgrade your manicure with a durable gel polish.'
        }
      ],
      popularDesigns: [
        {
          name: 'French Tips',
          description: 'Classic and elegant white tips',
          link:'https://i.pinimg.com/736x/88/01/74/88017496b1766b005d72b9098de01232.jpg'
        },
        {
          name: 'Ombre Nails',
          description: 'Beautiful gradient color blend',
          link:'https://i.pinimg.com/736x/fe/de/c8/fedec83a7879e31fa4a134747980f56d.jpg'
        },
        {
          name: 'Nail Art',
          description: 'Custom designs and patterns',
          link:'https://i.pinimg.com/1200x/9c/bb/b8/9cbbb8dfa2e5f11dbb1fd54b5fe6b9ce.jpg'
        },
        {
          name: 'Chrome Finish',
          description: 'Mirror-like metallic shine',
          link:'https://i.pinimg.com/736x/41/4a/05/414a0501098b2a8bef923b45a69ea9d6.jpg'
        }
      ]
    }
  },
  mounted() {
    // Trigger animations when component is mounted
    setTimeout(() => {
      this.isVisible = true;
    }, 100);
    
    // Add scroll animations
    window.addEventListener('scroll', this.handleScroll);
    this.handleScroll(); // Check on initial load
  },
  beforeDestroy() {
    window.removeEventListener('scroll', this.handleScroll);
  },
  methods: {
    handleScroll() {
      const elements = document.querySelectorAll('.animate-on-scroll');
      
      elements.forEach(element => {
        const elementTop = element.getBoundingClientRect().top;
        const elementBottom = element.getBoundingClientRect().bottom;
        
        if (elementTop < window.innerHeight && elementBottom > 0) {
          element.classList.add('animate-fade-in-up');
        }
      });
    }
  }
}
</script>

<style scoped>
.hero-section {
  background: linear-gradient(135deg, #FFFFFF 0%, #FFFDF7 100%);
  position: relative;
}

/* Animation classes */
@keyframes fadeInDown {
  from {
    opacity: 0;
    transform: translateY(-20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

@keyframes scaleIn {
  from {
    transform: scale(0.8);
    opacity: 0;
  }
  to {
    transform: scale(1);
    opacity: 1;
  }
}

@keyframes float {
  0% {
    transform: translateY(0px);
  }
  50% {
    transform: translateY(-10px);
  }
  100% {
    transform: translateY(0px);
  }
}

@keyframes bounceSlow {
  0%, 100% {
    transform: translateY(0) rotate(6deg);
  }
  50% {
    transform: translateY(-5px) rotate(6deg);
  }
}

.animate-fade-in-down {
  animation: fadeInDown 0.8s ease forwards;
}

.animate-fade-in-up {
  animation: fadeInUp 0.8s ease forwards;
  opacity: 0;
}

.animate-fade-in {
  animation: fadeIn 0.8s ease forwards;
  opacity: 0;
}

.animate-scale-in {
  animation: scaleIn 0.8s ease forwards;
  opacity: 0;
}

.animate-float {
  animation: float 4s ease-in-out infinite;
}

.animate-bounce-slow {
  animation: bounceSlow 3s ease-in-out infinite;
}

.animation-delay-200 {
  animation-delay: 0.2s;
}

.animation-delay-300 {
  animation-delay: 0.3s;
}

.animation-delay-400 {
  animation-delay: 0.4s;
}

.animation-delay-500 {
  animation-delay: 0.5s;
}

.animation-delay-600 {
  animation-delay: 0.6s;
}

.animation-delay-700 {
  animation-delay: 0.7s;
}

.animation-delay-800 {
  animation-delay: 0.8s;
}

/* Scroll animations */
.animate-on-scroll {
  opacity: 0;
  transition: opacity 0.6s ease, transform 0.6s ease;
}

.animate-on-scroll.visible {
  opacity: 1;
  transform: translateY(0);
}

.design-image {
  width: 100%;
  height: 100%;
  border-radius: 0.75rem;
  transition: transform 0.3s ease;
  object-fit: cover;
}

.group:hover .design-image {
  transform: scale(1.05);
}

.design-image {
  width: 100%;
  height: 200px; /* exact consistent height */
  border-radius: 0.75rem; /* same rounded-xl radius */
  transition: transform 0.3s ease;
  object-fit: cover;
}

.group:hover .design-image {
  transform: scale(1.05);
}
</style>