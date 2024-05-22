<template>
  <div id="app">
    <h1>Toko Produk</h1>
    <DaftarProduk :produkList="produkList" @produk-dipilih="tampilkanDetailProduk" />
    <DetailProduk :produk="produkTerpilih">
      <template v-slot:pesan-tambahan>
        <p v-if="produkTerpilih"><strong>Info Tambahan:</strong> Dapatkan diskon 10% untuk pembelian hari ini!</p>
        <p v-if="produkTerpilih"><strong>Garansi:</strong> Produk ini dilengkapi dengan garansi resmi selama 1 tahun.</p>
      </template>
      <template v-slot:tombol-aksi="{ produk }">
        <button class="beli-button" @click="beliProduk(produk)">Beli Produk Sekarang</button>
        <button class="keranjang-button" @click="tambahKeKeranjang(produk)">Tambah ke Keranjang</button>
      </template>
    </DetailProduk>
  </div>
</template>


<script>
import DaftarProduk from './components/DaftarProduk.vue';
import DetailProduk from './components/DetailProduk.vue';

export default {
  components: {
    DaftarProduk,
    DetailProduk
  },
  data() {
    return {
      produkList: [
        { id: 1, nama: 'iPhone 13', deskripsi: 'Smartphone terbaru dari Apple dengan layar Super Retina XDR 6.1 inci.', harga: 15000000 },
        { id: 2, nama: 'Samsung Galaxy S21', deskripsi: 'Ponsel canggih dengan layar Dynamic AMOLED 2X dan prosesor Exynos 2100.', harga: 13000000 },
        { id: 3, nama: 'MacBook Pro 14"', deskripsi: 'Laptop profesional dengan chip Apple M1 Pro, layar Retina 14 inci.', harga: 30000000 },
        { id: 4, nama: 'Sony WH-1000XM4', deskripsi: 'Headphone nirkabel dengan peredam bising aktif dan kualitas suara premium.', harga: 4500000 },
      ],
      produkTerpilih: null
    };
  },
  methods: {
    tampilkanDetailProduk(produk) {
      this.produkTerpilih = produk;
    },
    beliProduk(produk) {
      alert(`Anda telah membeli ${produk.nama} seharga Rp${produk.harga.toLocaleString()}`);
    },
    tambahKeKeranjang(produk) {
      alert(`${produk.nama} telah ditambahkan ke keranjang Anda.`);
    }
  }
}
</script>

<style>
#app {
  font-family: Arial, sans-serif;
  margin: 20px;
  background-color: #f5f5f5;
  padding: 20px;
  border-radius: 8px;
}
h1 {
  color: #333;
  font-size: 32px;
  margin-bottom: 20px;
  text-align: center;
}
.beli-button, .keranjang-button {
  padding: 10px 20px;
  margin-top: 10px;
  margin-right: 10px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s, box-shadow 0.3s;
}
.beli-button {
  background-color: #4CAF50;
  color: white;
}
.beli-button:hover {
  background-color: #45a049;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}
.keranjang-button {
  background-color: #008CBA;
  color: white;
}
.keranjang-button:hover {
  background-color: #007bb5;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}
</style>
