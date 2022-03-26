<template>
  <div>
    <select class="form-control mb-3 rounded-pill" v-model="selectedPembaca">
      <option value="" selected="selected">Pilih pembaca</option>
      <option v-for="(pembaca, i) in listPembaca" :key="i" :value="pembaca">{{ pembaca }}</option>
    </select>
    <select class="form-control rounded-pill" v-model="selectedBuku">
      <option value="" disabled="disabled" selected="selected">Pilih Buku</option>
      <option v-for="(buku, i) in listBuku" :key="i" :value="buku">{{ buku }}</option>
    </select>
    <button type="button" class="btn btn-outline-primary rounded-pill ml-3" style="width: 50px;" @click="addPair();">
      +
    </button>
    <ul class="list-group list-group-flush mt-3" type="riwayat baca">
      <li v-for="(pair, i) in listPair" :key="i" class="list-group-item d-flex justify-content-between align-items-center" style="padding: 0.75rem 0.25rem;">
        {{ pair.pembaca }} - {{ pair.buku }}
        <button class="btn btn-outline-danger rounded-pill" @click="hapusPair(i)">
          -
        </button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'InputSelect',
  data () {
    return {
      listBuku: [],
      listPembaca: [],
      listPair: [],
      selectedBuku: '',
      selectedPembaca: ''
    }
  },
  created () {
    this.$nuxt.$on('add-buku', (buku) => {
      this.listBuku.push(buku)
    })
    this.$nuxt.$on('add-pembaca', (pembaca) => {
      this.listPembaca.push(pembaca)
    })
    this.$nuxt.$on('hapus-buku', (buku) => {
      this.listBuku.splice(this.listBuku.indexOf(buku), 1)
    })
    this.$nuxt.$on('hapus-pembaca', (pembaca) => {
      this.listPembaca.splice(this.listPembaca.indexOf(pembaca), 1)
    })
  },
  methods: {
    addPair () {
      this.listPair.push({
        pembaca: this.selectedPembaca,
        buku: this.selectedBuku
      })
    },
    hapusPair (index) {
      this.$swal.fire({
        title: 'Apakah kamu yakin?',
        icon: 'warning',
        html: `menghapus data ${this.listPair[index].pembaca} - ${this.listPair[index].buku} dari daftar pembaca?`,
        showCancelButton: true,
        confirmButtonColor: '#3085d6',
        cancelButtonColor: '#d33',
        confirmButtonText: 'Hapus Aja'
      }).then((result) => {
        if (result.isConfirmed) {
          this.listPair.splice(index, 1)
        }
      })
    }
  }
}
</script>
