<template>
  <div class="py-12 bg-gradient-to-b from-white to-yellow-50 min-h-screen">
    <div class="container mx-auto px-4">
      <div class="text-center mb-10">
        <h1 class="text-4xl font-bold mb-4 text-yellow-600">Book an Appointment</h1>
        <p class="text-gray-600 max-w-2xl mx-auto">
          Schedule your nail service with our easy-to-use booking system.
        </p>
      </div>

      <div class="max-w-3xl mx-auto">
        <div class="bg-white rounded-xl shadow-lg p-8 border border-yellow-100">
          <form @submit.prevent="submitAppointment">
            <!-- 步骤指示器 -->
            <div class="mb-10">
              <div class="flex justify-between items-center relative">
                <div
                  v-for="(step, index) in steps"
                  :key="index"
                  class="flex flex-col items-center z-10"
                  :class="{ 'text-yellow-600': currentStep >= index }"
                >
                  <div
                    class="step-circle flex items-center justify-center mb-2"
                    :class="{ 'active': currentStep >= index }"
                  >
                    <span v-if="currentStep > index" class="text-white">
                      <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"></path>
                      </svg>
                    </span>
                    <span v-else>{{ index + 1 }}</span>
                  </div>
                  <span class="text-sm font-medium">{{ step }}</span>
                </div>
                <div class="absolute top-5 left-0 right-0 h-1 bg-gray-200 -z-10">
                  <div 
                    class="h-full bg-yellow-600 transition-all duration-500" 
                    :style="{ width: `${(currentStep / (steps.length - 1)) * 100}%` }"
                  ></div>
                </div>
              </div>
            </div>

            <!-- 步骤 1: 选择服务 -->
            <div v-if="currentStep === 0" class="animate-fadeIn">
              <h2 class="text-2xl font-bold mb-6 text-yellow-600">Select Service</h2>
              
              <div class="space-y-4 mb-8">
                <div
                  v-for="(service, index) in services"
                  :key="index"
                  class="service-option p-5 rounded-xl border-2 cursor-pointer transition-all duration-300"
                  :class="{ 'border-yellow-500 bg-yellow-50 shadow-md': appointment.service === service.name }"
                  @click="appointment.service = service.name"
                >
                  <div class="flex justify-between items-center">
                    <div>
                      <h3 class="font-bold text-lg">{{ service.name }}</h3>
                      <p class="text-gray-600 text-sm mt-1">{{ service.description }}</p>
                    </div>
                    <div class="text-right">
                      <span class="font-bold text-yellow-600 text-lg">{{ service.price }}</span>
                      <div class="flex flex-wrap justify-end mt-1">
                        <span
                          v-for="(tag, tagIndex) in service.tags"
                          :key="tagIndex"
                          class="inline-block bg-yellow-100 text-yellow-800 text-xs px-2 py-1 rounded ml-1 mb-1"
                        >
                          {{ tag }}
                        </span>
                      </div>
                    </div>
                  </div>
                </div>
              </div>

              <div class="mb-8">
                <h3 class="font-bold mb-4 text-lg">Add-On Services</h3>
                <div class="grid grid-cols-1 md:grid-cols-2 gap-3">
                  <label 
                    v-for="(addon, index) in addons"
                    :key="index"
                    class="flex items-center p-4 rounded-lg border border-gray-200 hover:bg-yellow-50 cursor-pointer transition-colors"
                  >
                    <input
                      type="checkbox"
                      v-model="appointment.addons"
                      :value="addon.name"
                      class="h-5 w-5 text-yellow-600 rounded focus:ring-yellow-500"
                    >
                    <div class="ml-3">
                      <span class="font-medium">{{ addon.name }}</span>
                      <span class="text-yellow-600 font-medium ml-2">{{ addon.price }}</span>
                    </div>
                  </label>
                </div>
              </div>

              <div>
                <h3 class="font-bold mb-4 text-lg">Service Location</h3>
                <div class="space-y-3">
                  <label class="flex items-center p-4 rounded-xl border-2 border-gray-200 hover:border-yellow-300 cursor-pointer transition-colors">
                    <input
                      type="radio"
                      v-model="appointment.location"
                      value="salon"
                      class="h-5 w-5 text-yellow-600 focus:ring-yellow-500"
                    >
                    <div class="ml-4">
                      <span class="font-medium text-lg">Salon Visit</span>
                      <p class="text-gray-600 text-sm">Visit our salon for your appointment</p>
                    </div>
                  </label>
                  <label class="flex items-center p-4 rounded-xl border-2 border-gray-200 hover:border-yellow-300 cursor-pointer transition-colors">
                    <input
                      type="radio"
                      v-model="appointment.location"
                      value="home"
                      class="h-5 w-5 text-yellow-600 focus:ring-yellow-500"
                    >
                    <div class="ml-4">
                      <span class="font-medium text-lg">Home Service</span>
                      <p class="text-gray-600 text-sm">We'll come to your location (+P300)</p>
                    </div>
                  </label>
                </div>
              </div>
            </div>

            <!-- 步骤 2: 选择日期和时间 -->
            <div v-if="currentStep === 1" class="animate-fadeIn">
              <h2 class="text-2xl font-bold mb-6 text-yellow-600">Select Date & Time</h2>
              
              <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                <div>
                  <h3 class="font-bold mb-4 text-lg">Choose Date</h3>
                  <div class="bg-gray-50 p-4 rounded-xl">
                    <input
                      type="date"
                      v-model="appointment.date"
                      :min="minDate"
                      class="w-full p-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-yellow-600 focus:border-yellow-600 text-lg"
                    >
                    <div class="mt-4 text-center">
                      <p class="text-gray-600 mb-2">Selected Date</p>
                      <p class="text-xl font-bold text-yellow-600">{{ formatDate(appointment.date) }}</p>
                    </div>
                  </div>
                </div>
                <div>
                  <h3 class="font-bold mb-4 text-lg">Available Time Slots</h3>
                  <div class="bg-gray-50 p-4 rounded-xl">
                    <div class="grid grid-cols-3 gap-3 max-h-80 overflow-y-auto p-1">
                      <button
                        v-for="(time, index) in availableTimes"
                        :key="index"
                        type="button"
                        class="py-3 px-2 rounded-lg text-sm font-medium border transition-all duration-200"
                        :class="appointment.time === time ? 'bg-yellow-600 text-white border-yellow-600 shadow-md' : 'border-gray-300 hover:bg-gray-100'"
                        @click="appointment.time = time"
                      >
                        {{ time }}
                      </button>
                    </div>
                    <div v-if="appointment.time" class="mt-4 text-center">
                      <p class="text-gray-600 mb-2">Selected Time</p>
                      <p class="text-xl font-bold text-yellow-600">{{ appointment.time }}</p>
                    </div>
                  </div>
                </div>
              </div>
            </div>

            <!-- 步骤 3: 个人信息 -->
            <div v-if="currentStep === 2" class="animate-fadeIn">
              <h2 class="text-2xl font-bold mb-6 text-yellow-600">Your Information</h2>
              
              <div class="space-y-5">
                <div>
                  <label class="block text-sm font-medium text-gray-700 mb-2">Full Name</label>
                  <input
                    type="text"
                    v-model="appointment.name"
                    required
                    placeholder="Enter your full name"
                    class="w-full p-4 border border-gray-300 rounded-lg focus:ring-2 focus:ring-yellow-600 focus:border-yellow-600"
                  >
                </div>

                <div>
                  <label class="block text-sm font-medium text-gray-700 mb-2">Phone Number</label>
                  <input
                    type="tel"
                    v-model="appointment.phone"
                    required
                    placeholder="Enter your phone number"
                    class="w-full p-4 border border-gray-300 rounded-lg focus:ring-2 focus:ring-yellow-600 focus:border-yellow-600"
                  >
                </div>

                <div>
                  <label class="block text-sm font-medium text-gray-700 mb-2">Email Address</label>
                  <input
                    type="email"
                    v-model="appointment.email"
                    required
                    placeholder="Enter your email address"
                    class="w-full p-4 border border-gray-300 rounded-lg focus:ring-2 focus:ring-yellow-600 focus:border-yellow-600"
                  >
                </div>

                <div>
                  <label class="block text-sm font-medium text-gray-700 mb-2">Special Requests or Notes</label>
                  <textarea
                    v-model="appointment.notes"
                    rows="4"
                    placeholder="Any special requests or notes for your appointment"
                    class="w-full p-4 border border-gray-300 rounded-lg focus:ring-2 focus:ring-yellow-600 focus:border-yellow-600"
                  ></textarea>
                </div>

                <div class="flex items-start p-4 bg-yellow-50 rounded-lg">
                  <input
                    type="checkbox"
                    v-model="appointment.terms"
                    required
                    class="h-5 w-5 text-yellow-600 rounded focus:ring-yellow-500 mt-1"
                  >
                  <label class="ml-3 text-sm text-gray-700">
                    I agree to the
                    <a href="#" class="text-yellow-600 hover:text-yellow-700 font-medium">terms and conditions</a>
                    and understand the cancellation policy.
                  </label>
                </div>
              </div>
            </div>

            <!-- 步骤 4: 确认预约 -->
            <div v-if="currentStep === 3" class="animate-fadeIn">
              <h2 class="text-2xl font-bold mb-6 text-yellow-600">Confirm Your Appointment</h2>
              
              <div class="bg-gradient-to-br from-yellow-50 to-white rounded-xl p-6 mb-8 border border-yellow-200 shadow-sm">
                <div class="space-y-4">
                  <div class="flex justify-between pb-3 border-b border-yellow-100">
                    <span class="font-bold text-gray-700">Service:</span>
                    <span class="font-medium">{{ appointment.service }}</span>
                  </div>
                  <div v-if="appointment.addons.length > 0" class="flex justify-between pb-3 border-b border-yellow-100">
                    <span class="font-bold text-gray-700">Add-ons:</span>
                    <span class="font-medium">{{ appointment.addons.join(', ') }}</span>
                  </div>
                  <div class="flex justify-between pb-3 border-b border-yellow-100">
                    <span class="font-bold text-gray-700">Location:</span>
                    <span class="font-medium">{{ appointment.location === 'home' ? 'Home Service' : 'Salon' }}</span>
                  </div>
                  <div class="flex justify-between pb-3 border-b border-yellow-100">
                    <span class="font-bold text-gray-700">Date:</span>
                    <span class="font-medium">{{ formatDate(appointment.date) }}</span>
                  </div>
                  <div class="flex justify-between pb-3 border-b border-yellow-100">
                    <span class="font-bold text-gray-700">Time:</span>
                    <span class="font-medium">{{ appointment.time }}</span>
                  </div>
                  <div class="flex justify-between pb-3 border-b border-yellow-100">
                    <span class="font-bold text-gray-700">Name:</span>
                    <span class="font-medium">{{ appointment.name }}</span>
                  </div>
                  <div class="flex justify-between pb-3 border-b border-yellow-100">
                    <span class="font-bold text-gray-700">Phone:</span>
                    <span class="font-medium">{{ appointment.phone }}</span>
                  </div>
                  <div class="pt-3">
                    <div class="flex justify-between">
                      <span class="font-bold text-lg text-gray-800">Total:</span>
                      <span class="font-bold text-xl text-yellow-600">{{ calculateTotal() }}</span>
                    </div>
                  </div>
                </div>
              </div>

              <div class="text-center mb-6">
                <div class="inline-flex items-center bg-blue-50 text-blue-800 rounded-lg p-4 mb-4">
                  <svg class="w-6 h-6 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 16h-1v-4h-1m1-4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z"></path>
                  </svg>
                  <p>A confirmation message will be sent to your phone number.</p>
                </div>
                <button
                  type="submit"
                  class="bg-yellow-600 text-white px-8 py-4 rounded-full font-bold text-lg hover:bg-yellow-700 transition-colors shadow-lg hover:shadow-xl flex items-center justify-center mx-auto"
                  :disabled="loading"
                >
                  <span v-if="loading" class="flex items-center">
                    <svg class="animate-spin -ml-1 mr-3 h-5 w-5 text-white" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24">
                      <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle>
                      <path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"></path>
                    </svg>
                    Processing...
                  </span>
                  <span v-else class="flex items-center">
                    <svg class="w-5 h-5 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"></path>
                    </svg>
                    Confirm Booking
                  </span>
                </button>
              </div>
            </div>

            <!-- 导航按钮 -->
            <div class="flex justify-between mt-10">
              <button
                v-if="currentStep > 0"
                type="button"
                class="px-6 py-3 border border-yellow-600 text-yellow-600 rounded-full font-medium hover:bg-yellow-50 transition-colors flex items-center"
                @click="prevStep"
              >
                <svg class="w-5 h-5 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7"></path>
                </svg>
                Back
              </button>
              <div v-else></div>
              <button
                v-if="currentStep < steps.length - 1"
                type="button"
                class="bg-yellow-600 text-white px-6 py-3 rounded-full font-medium hover:bg-yellow-700 transition-colors flex items-center"
                @click="nextStep"
                :disabled="!canProceed"
              >
                Next
                <svg class="w-5 h-5 ml-2" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"></path>
                </svg>
              </button>
            </div>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Appointments',
  data() {
    return {
      loading: false,
      currentStep: 0,
      steps: ['Service', 'Date & Time', 'Information', 'Confirm'],
      minDate: new Date().toISOString().substr(0, 10),
      availableTimes: [
        '9:00 AM', '10:00 AM', '11:00 AM', '12:00 PM', 
        '1:00 PM', '2:00 PM', '3:00 PM', '4:00 PM', '5:00 PM'
      ],
      appointment: {
        service: '',
        addons: [],
        location: 'salon',
        date: new Date().toISOString().substr(0, 10),
        time: '',
        name: '',
        phone: '',
        email: '',
        notes: '',
        terms: false
      },
      services: [
        {
          name: 'Gel Polish',
          price: 'P300',
          description: 'Includes gel application, cuticle care, and basic nail shaping.',
          tags: ['60 min', 'Gel', 'Manicure']
        },
        {
          name: 'Gel Overlay',
          price: 'P350',
          description: 'Strengthens natural nails with a layer of gel polish.',
          tags: ['45 min', 'Gel', 'Natural Nails']
        },
        {
          name: 'Soft Gel Extensions',
          price: 'P500',
          description: 'Adds length to natural nails using soft gel tips.',
          tags: ['90 min', 'Extensions', 'Soft Gel']
        },
        {
          name: 'Dual Form Extensions',
          price: 'P500',
          description: 'Creates extensions using dual forms for a perfect shape.',
          tags: ['120 min', 'Extensions', 'Dual Form']
        },
        {
          name: 'Lash Lift',
          price: 'P300',
          description: 'Enhances natural lashes with a lifting and tinting service.',
          tags: ['60 min', 'Lashes', 'Semi-permanent']
        },
        {
          name: 'Nail Repair',
          price: 'P150',
          description: 'Fix broken or damaged nails with professional repair techniques.',
          tags: ['30 min', 'Repair', 'Damaged Nails']
        }
      ],
      addons: [
        {
          name: 'Nail Art (Simple)',
          price: 'P50'
        },
        {
          name: 'Nail Art (Complex)',
          price: 'P100'
        },
        {
          name: 'French Tips',
          price: 'P50'
        },
        {
          name: 'Charms ',
          price: 'P50+'
        },
        {
          name: 'Ombre',
          price: 'P50'
        },
        {
          name: 'Nail Strengthener',
          price: 'P100'
        },
         {
          name: '3D Sculpt',
          price: 'P50'
        }
      ]
    }
  },
  computed: {
    canProceed() {
      if (this.currentStep === 0) {
        return this.appointment.service !== ''
      } else if (this.currentStep === 1) {
        return this.appointment.date !== '' && this.appointment.time !== ''
      } else if (this.currentStep === 2) {
        return this.appointment.name !== '' && this.appointment.phone !== '' && 
               this.appointment.email !== '' && this.appointment.terms
      }
      return true
    }
  },
  methods: {
    nextStep() {
      if (this.canProceed) {
        this.currentStep++
        window.scrollTo(0, 0)
      }
    },
    prevStep() {
      this.currentStep--
      window.scrollTo(0, 0)
    },
    formatDate(date) {
      const options = { year: 'numeric', month: 'long', day: 'numeric', weekday: 'long' }
      return new Date(date).toLocaleDateString(undefined, options)
    },
    calculateTotal() {
      let total = 0
      
      // 添加服务价格
      const service = this.services.find(s => s.name === this.appointment.service)
      if (service) {
        // 移除货币符号和逗号，转换为数字
        const price = parseInt(service.price.replace(/[^\d]/g, ''))
        total += price
      }
      
      // 添加附加服务价格
      this.appointment.addons.forEach(addonName => {
        const addon = this.addons.find(a => a.name === addonName)
        if (addon) {
          // 对于有"+"的价格，我们使用最小值
          const price = parseInt(addon.price.replace(/[^\d]/g, ''))
          total += price
        }
      })
      
      // 添加家庭服务费
      if (this.appointment.location === 'home') {
        total += 300
      }
      
      return `P${total.toLocaleString()}`
    },
    submitAppointment() {
      if (this.canProceed) {
        this.loading = true
        
        // 模拟API调用
        setTimeout(() => {
          // 保存预约数据到localStorage
          const appointments = JSON.parse(localStorage.getItem('appointments') || '[]')
          const newAppointment = {
            ...this.appointment,
            id: Date.now(),
            createdAt: new Date().toISOString()
          }
          appointments.push(newAppointment)
          localStorage.setItem('appointments', JSON.stringify(appointments))
          
          this.loading = false
          
          // 显示成功消息并重置表单
          alert('Your appointment has been booked successfully! You will receive a confirmation message shortly.')
          this.resetForm()
          this.currentStep = 0
          
          // 可选：重定向到首页
          // this.$router.push('/')
        }, 1500)
      }
    },
    resetForm() {
      this.appointment = {
        service: '',
        addons: [],
        location: 'salon',
        date: new Date().toISOString().substr(0, 10),
        time: '',
        name: '',
        phone: '',
        email: '',
        notes: '',
        terms: false
      }
    }
  }
}
</script>

<style scoped>
.step-circle {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background-color: #f0f0f0;
  color: #999;
  font-weight: bold;
  transition: all 0.3s ease;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.step-circle.active {
  background-color: var(--primary-color);
  color: white;
  box-shadow: 0 4px 6px rgba(212, 175, 55, 0.3);
}

.service-option {
  border: 1px solid var(--border-color);
  transition: all 0.3s ease;
}

.service-option:hover {
  border-color: var(--primary-color);
  transform: translateY(-2px);
}

@keyframes fadeIn {
  from { opacity: 0; transform: translateY(10px); }
  to { opacity: 1; transform: translateY(0); }
}

.animate-fadeIn {
  animation: fadeIn 0.5s ease forwards;
}
</style>