<script setup>
import { defineProps, defineEmits  } from 'vue';
import { Link, router } from '@inertiajs/vue3';

const props = defineProps({
  product: {
    type: Object,
    required: true,
  },
});

const emit = defineEmits(['add-to-cart']);

const addToCartHandler = () => {
  // Emit the 'add-to-cart' event with the product id
  emit('add-to-cart', props.product.id_produk);
};
</script>

<template>
  <div class="flex flex-col bg-white rounded-lg shadow-md hover:shadow-lg hover-anim">
    <div class="flex justify-center w-full bg-gray-100 rounded-t-md overflow-hidden">
      <img :src="`storage/${props.product.gambar}`"
        class="self-center w-60 h-40 bg-white transition-transform duration-300 transform hover:scale-110 object-cover" alt="">
    </div>
    <div class="flex flex-col p-3 h-36 space-y-1">
      <div class="font-semibold truncate max-w-full">Rp. {{ props.product.harga.toLocaleString() }}</div>
      <h3 class="line-clamp-2 max-w-full">{{ props.product.nama_produk }}</h3>
      <p class="text-xs line-clamp-2 max-w-full">{{ props.product.deskripsi }}</p>
      <button v-if="$page.props.auth.user" @click="addToCartHandler" 
        class="self-end font-semibold p-2 rounded-md bg-amber-300 hover:bg-amber-400 hover-anim">
        + Keranjang
      </button>
      <Link v-else :href="route('login')" 
        class="self-end font-semibold p-2 rounded-md bg-amber-300 hover:bg-amber-400 hover-anim">
        + Keranjang
    </Link>
    </div>
  </div>
</template>

<script>

</script>

<!-- <script lang="ts">
import { defineComponent, PropType } from "vue";

interface Product {
  price: number;
  name: string;
  description: string;
  image: string;
}

export default defineComponent({
  name: "ProductCard",
  props: {
    product: {
      type: Object as PropType<Product>,
      required: true,
    },
  },
  methods: {
    buy() {
      console.log("Membeli produk:", this.product);
    },
  },
});
</script> -->

<!-- <style scoped>
.product-card {
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  border-radius: 15px;
  padding: 20px;
  width: 300px;
  height: 400px;
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
  position: relative;
  color: #fff;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  font-family: "Poppins", sans-serif;
  overflow: hidden;
}

.product-info {
  background: rgba(0, 0, 0, 0.6);
  border-radius: 12px;
  padding: 15px;
  text-align: center;
}

.product-price {
  font-weight: 700;
  font-size: 16px;
  margin-bottom: 5px;
  text-transform: uppercase;
}

.product-name {
  font-size: 18px;
  font-weight: 600;
  margin: 5px 0;
}

.product-description {
  font-size: 14px;
  margin-bottom: 10px;
}

.product-button {
  background-color: #fff;
  color: #000;
  border: none;
  border-radius: 20px;
  padding: 10px 20px;
  font-weight: 600;
  font-size: 14px;
  cursor: pointer;
  text-transform: uppercase;
}

.product-button:hover {
  background-color: #f15a24;
  color: #fff;
}
</style> -->
