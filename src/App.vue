<template>
  <main class="app">
    <section :class="pageClass" class="page">
      <Loader v-if="loading" />

      <div v-else class="content-container">
        <ProductDisplay
          v-if="product"
          :product="product"
          @next="nextProduct"
        />

        <div v-else class="unavailable-container">
          <div class="unavailable-card">
            <img :src="sadFaceIcon" alt="Unavailable Product" class="sad-face-icon" />
            <p class="unavailable-text">This product is unavailable to show</p>
            <button class="unavailable-next-btn" @click="nextProduct">
              Next product
            </button>
          </div>
        </div>
      </div>
    </section>
  </main>
</template>

<script setup>
import { ref, computed, onMounted } from 'vue'
import Loader from './components/Loader.vue'
import sadFaceIcon from './assets/sad-face.png'
import ProductDisplay from './components/ProductDisplay.vue'

const index = ref(0)
const product = ref(null)
const loading = ref(true)

const pageClass = computed(() => {
  if (loading.value || !product.value) {
    return 'page-unavailable-bg';
  }
  const cat = product.value.category;
  if (cat === "men's clothing") return 'page-men';
  if (cat === "women's clothing") return 'page-women';
  return 'page-unavailable-bg';
});

async function fetchProductByIndex(i) {
  loading.value = true;
  product.value = null;
  try {
    const res = await fetch(`https://fakestoreapi.com/products/${i}`);
    if (!res.ok) throw new Error(`HTTP ${res.status}`);
    const data = await res.json();
    
    if (data.category === "men's clothing" || data.category === "women's clothing") {
      product.value = data;
    } else {
      product.value = null;
    }
  } catch (err) {
    console.error('Fetch error:', err);
    product.value = null;
  } finally {
    loading.value = false;
  }
}

function nextProduct() {
  index.value = index.value >= 20 ? 1 : index.value + 1;
  fetchProductByIndex(index.value);
}

onMounted(() => {
  nextProduct();
});
</script>

<style>
.page {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 20px;
  box-sizing: border-box;
  transition: background 0.5s ease;
}

.content-container {
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.page-men {
  background: 
    url('/src/assets/bg-pattern.svg') repeat, 
    linear-gradient( 
      to bottom,
      var(--bg-men-style-color) 0%,
      var(--bg-men-style-color) 70%,
      var(--primary-color) 70%,
      var(--primary-color) 100%
    );
}

.page-women {
  background: 
    url('/src/assets/bg-pattern.svg') repeat, 
    linear-gradient( 
      to bottom,
      var(--bg-women-style-color) 0%,
      var(--bg-women-style-color) 70%,
      var(--primary-color) 70%,
      var(--primary-color) 100%
    );
}

.page-unavailable-bg {
  background:
    linear-gradient(
      to bottom,
      var(--bg-unavailable-top) 0%,
      var(--bg-unavailable-top) 70%,
      var(--primary-color) 70%,
      var(--primary-color) 100%
    );
}

.unavailable-container {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
}
</style>