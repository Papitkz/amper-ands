<template>
  <div class="py-12">
    <v-container>
      <v-row>
        <v-col cols="12" class="text-center mb-10">
          <h1 class="text-4xl font-weight-bold mb-4" style="color: var(--primary-color);">Our Works</h1>
          <p class="text-gray-600 max-w-2xl mx-auto">
            Explore our portfolio of stunning nail designs and artistry.
          </p>
        </v-col>
      </v-row>

      <!-- 作品分类 -->
      <v-row>
        <v-col cols="12" class="mb-8">
          <div class="d-flex flex-wrap justify-center">
            <v-btn
              v-for="(category, index) in categories"
              :key="index"
              class="ma-2 text-capitalize"
              :color="selectedCategory === category ? 'primary' : 'white'"
              :outlined="selectedCategory !== category"
              @click="selectedCategory = category"
            >
              {{ category }}
            </v-btn>
          </div>
        </v-col>
      </v-row>

      <!-- 作品网格 -->
      <v-row>
        <v-col
          cols="12"
          sm="6"
          md="4"
          lg="3"
          v-for="(work, index) in filteredWorks"
          :key="index"
          class="mb-6"
        >
          <div class="girlie-card overflow-hidden">
            <v-img
              :src="work.image"
              height="250"
              class="align-end"
            >
              <div class="pa-4" style="background: linear-gradient(to top, rgba(0,0,0,0.7), transparent);">
                <h3 class="text-white font-weight-bold">{{ work.title }}</h3>
                <p class="text-white text-caption">{{ work.category }}</p>
              </div>
            </v-img>
            <div class="pa-4">
              <p class="text-gray-600 mb-3">{{ work.description }}</p>
              <div class="d-flex justify-space-between align-center">
                <div>
                  <v-chip
                    v-for="(tag, tagIndex) in work.tags"
                    :key="tagIndex"
                    class="mr-2 mb-2"
                    x-small
                    style="background-color: rgba(212, 175, 55, 0.1); color: var(--primary-color);"
                  >
                    {{ tag }}
                  </v-chip>
                </div>
                <v-btn
                  icon
                  small
                  style="color: var(--primary-color);"
                >
                  <v-icon>mdi-heart-outline</v-icon>
                </v-btn>
              </div>
            </div>
          </div>
        </v-col>
      </v-row>

      <!-- 加载更多按钮 -->
      <v-row>
        <v-col cols="12" class="text-center">
          <v-btn
            large
            outlined
            class="text-capitalize"
            style="color: var(--primary-color); border-color: var(--primary-color);"
          >
            Load More
          </v-btn>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
  name: 'Works',
  data() {
    return {
      selectedCategory: 'All',
      categories: ['All', 'Gel Nails', 'Extensions', 'Nail Art', 'Bridal'],
      works: [
        {
          title: 'Elegant French',
          category: 'Gel Nails',
          description: 'Classic French tips with a modern twist.',
          image: 'https://images.unsplash.com/photo-1610992015732-2c9f0ece5f8c?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80',
          tags: ['Classic', 'Elegant']
        },
        {
          title: 'Glitter Glam',
          category: 'Nail Art',
          description: 'Sparkling glitter design perfect for special occasions.',
          image: 'https://images.unsplash.com/photo-1564185839287-8f7c27c9c5e2?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80',
          tags: ['Glitter', 'Party']
        },
        {
          title: 'Floral Fantasy',
          category: 'Nail Art',
          description: 'Delicate hand-painted floral design.',
          image: 'https://images.unsplash.com/photo-1610992015732-2c9f0ece5f8c?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80',
          tags: ['Floral', 'Hand-painted']
        },
        {
          title: 'Bridal Bliss',
          category: 'Bridal',
          description: 'Elegant design perfect for your special day.',
          image: 'https://images.unsplash.com/photo-1610992015732-2c9f0ece5f8c?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80',
          tags: ['Bridal', 'Pearls']
        },
        {
          title: 'Chrome Dreams',
          category: 'Gel Nails',
          description: 'Mirror-like chrome finish for a futuristic look.',
          image: 'https://images.unsplash.com/photo-1564185839287-8f7c27c9c5e2?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80',
          tags: ['Chrome', 'Metallic']
        },
        {
          title: 'Stiletto Extensions',
          category: 'Extensions',
          description: 'Bold stiletto-shaped nail extensions.',
          image: 'https://images.unsplash.com/photo-1610992015732-2c9f0ece5f8c?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80',
          tags: ['Stiletto', 'Bold']
        },
        {
          title: 'Minimalist Chic',
          category: 'Gel Nails',
          description: 'Clean and simple design for everyday elegance.',
          image: 'https://images.unsplash.com/photo-1564185839287-8f7c27c9c5e2?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80',
          tags: ['Minimalist', 'Clean']
        },
        {
          title: 'Ombre Magic',
          category: 'Gel Nails',
          description: 'Beautiful ombre blend from light to dark.',
          image: 'https://images.unsplash.com/photo-1610992015732-2c9f0ece5f8c?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80',
          tags: ['Ombre', 'Gradient']
        }
      ]
    }
  },
  computed: {
    filteredWorks() {
      if (this.selectedCategory === 'All') {
        return this.works
      }
      return this.works.filter(work => work.category === this.selectedCategory)
    }
  }
}
</script>