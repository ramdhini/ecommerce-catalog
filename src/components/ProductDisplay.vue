<template>
  <article class="product-card">
    <div class="image-wrap">
      <img :src="product.image" :alt="product.title" />
    </div>

    <div class="card-content">
      <h2 class="title">{{ product.title }}</h2>
      <div class="card-content-category">
        <h5>{{ product.category }}</h5>
        <div class="rating">
          <h5>{{ product.rating.rate }}/5</h5>
          <div class="card-product-rating">
            <div
              v-for="(star, index) in 5"
              :key="index"
              class="rating-circle"
              :class="{ 'active-rating': index < Math.round(product.rating.rate) }"
            ></div>
          </div>
        </div>
      </div>
      <hr class="divider" />
      <p class="description">{{ product.description }}</p>
       <hr class="divider" />
      <h5 class="price">${{ product.price }}</h5>
      <div class="card-actions">
        <button class="buy-btn">Buy now</button>
        <button class="next-btn-card" @click="$emit('next')">Next product</button>
      </div>
    </div>
  </article>
</template>

<script setup>
const props = defineProps({
  product: { type: Object, required: true }
})
</script>

<style scoped>
.product-card {
  display: flex;
  gap: 2rem;
  background: #fff;
  border-radius: 16px;
  padding: 2rem;
  box-shadow: 0 4px 16px rgba(0,0,0,0.1);
  width: 1000px;
  height: 500px;
  margin: 2rem auto;
}

.image-wrap {
  flex: 0 0 280px;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 1rem;
}

.image-wrap img {
  max-width: 100%;
  max-height: 320px;
  width: auto;
  height: auto;
  object-fit: contain;
  border-radius: 8px;
}

.card-content {
  flex: 1;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding: 0.5rem 0;
  gap: 0rem;
}

.title {
  font-size: 28px;
  font-weight: 600;
  color: var(--men-style-color);
  margin: 0;
  line-height: 1.2;
  margin-bottom: -1.5rem;
}

.card-content-category {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 0;
}

.card-content-category h5 {
  font-weight: 400;
  color: #666;
  font-size: 18px;
  margin: 0;
}

.rating {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-weight: 400;
  font-size: 18px;
}

.rating h5 {
  margin: 0;
}

.card-product-rating {
  display: flex;
  gap: 0.1rem;
}

.rating-circle {
  width: 18px;
  height: 18px;
  border-radius: 50%;
  border: 1px solid var(--men-style-color);
  background: var(--primary-color);
}

.active-rating {
  background: var(--men-style-color);
}

.description {
  color: #333;
  line-height: 1.5;
  font-weight: 400;
  font-size: 20px;
  margin: 0;
  flex-grow: 1;
  overflow-y: auto;
  max-height: 200px;
  padding: 0.5rem 0.5rem 0rem 0rem;
  
}

.price {
  font-size: 28px;
  font-weight: 600;
  color: var(--men-style-color);
  margin: 0;
}

.card-actions {
  display: flex;
  gap: 1rem;
  
}

.buy-btn {
  flex: 1;
  padding: 0.75rem 1.5rem;
  background: var(--men-style-color);
  color: var(--primary-color);
  border: none;
  border-radius: 6px;
  font-size: 20px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.2s ease;
}

.next-btn-card {
  flex: 1;
  padding: 0.75rem 1.5rem;
  background: var(--primary-color);
  color: var(--men-style-color);
  border: 2px solid var(--men-style-color);
  border-radius: 6px;
  font-size: 20px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.2s ease;
}

.buy-btn:hover {
  background: #163b8c;
}

.next-btn-card:hover {
  background: #f5f7fa;
}

.divider {
  border: none;
  border-top: 1px solid #e0e0e0;
  margin: -40px 0 -40px 0;
  width: 100%;
}

@media (max-width: 768px) {
  .product-card {
    flex-direction: column;
    width: 100%;
    height: auto;
    margin: 1rem;
    padding: 1.5rem;
  }
  
  .image-wrap {
    flex: none;
    height: 200px;
  }
  
  .title {
    font-size: 24px;
  }
  
  .price {
    font-size: 24px;
  }
  
  .description {
    max-height: 80px;
  }
}

.description::-webkit-scrollbar {
  width: 6px;
}

.description::-webkit-scrollbar-track {
  background: #f1f1f1;
  border-radius: 3px;
}

.description::-webkit-scrollbar-thumb {
  background: #ccc;
  border-radius: 3px;
}

.description::-webkit-scrollbar-thumb:hover {
  background: #999;
}
</style>