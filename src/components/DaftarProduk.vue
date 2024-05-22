<template>
  <div class="daftar-produk">
    <ItemProduk
      v-for="produk in produkList"
      :key="produk.id"
      :produk="produk"
      @produk-dipilih="tanganiProdukDipilih"
    />
  </div>
</template>

<script>
import ItemProduk from './ItemProduk.vue';

export default {
  components: { ItemProduk },
  props: ['produkList'],
  methods: {
    tanganiProdukDipilih(produk) {
      this.$emit('produk-dipilih', produk);
    }
  }
}
</script>

<style scoped>
.daftar-produk {
  display: flex;
  flex-direction: column;
  gap: 10px;
}
</style>
