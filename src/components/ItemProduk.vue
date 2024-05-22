<template>
  <div class="item-produk" @click="pilihProduk">
    {{ produk.nama }}
  </div>
</template>

<script>
export default {
  props: ['produk'],
  methods: {
    pilihProduk() {
      this.$emit('produk-dipilih', this.produk);
    }
  }
}
</script>

<style scoped>
.item-produk {
  padding: 15px;
  border: 1px solid #ddd;
  border-radius: 8px;
  margin-bottom: 10px;
  cursor: pointer;
  transition: background-color 0.3s, box-shadow 0.3s;
  font-size: 16px;
  background-color: #fff;
}
.item-produk:hover {
  background-color: #f9f9f9;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}
</style>
