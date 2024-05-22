<template>
  <div v-if="produk" class="detail-produk">
    <h2>{{ produk.nama }}</h2>
    <p>{{ produk.deskripsi }}</p>
    <p><strong>Harga:</strong> Rp{{ produk.harga.toLocaleString() }}</p>
    <slot name="pesan-tambahan">
      <p><strong>Info Tambahan:</strong> Tidak ada info tambahan untuk produk ini.</p>
    </slot>
    <slot name="tombol-aksi" :produk="produk">
      <button @click="beliProduk">Beli Sekarang</button>
    </slot>
  </div>
</template>

<script>
export default {
  props: ['produk'],
  methods: {
    beliProduk() {
      alert(`Anda telah membeli ${this.produk.nama}`);
    }
  }
}
</script>

<style scoped>
.detail-produk {
  margin-top: 20px;
  padding: 20px;
  border: 1px solid #ddd;
  border-radius: 8px;
  background-color: #fff;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}
.detail-produk h2 {
  margin-bottom: 10px;
  font-size: 24px;
  color: #333;
}
.detail-produk p {
  margin-bottom: 10px;
  font-size: 16px;
  color: #666;
}
</style>
