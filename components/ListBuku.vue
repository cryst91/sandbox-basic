<template>
  <div>
    <ul class="list-group list-group-flush mt-3" type="buku">
      <li v-for="(buku, i) in listBuku" :key="i" class="list-group-item d-flex justify-content-between align-items-center" style="padding: 0.75rem 0.25rem;">
        {{ buku }}
        <button class="btn btn-outline-danger rounded-pill" @click="hapusBuku(i)">
          -
        </button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'ListBuku',
  data () {
    return {
      listBuku: []
    }
  },
  created () {
    this.$nuxt.$on('add-buku', (buku) => {
      this.listBuku.push(buku)
    })
  },
  methods: {
    hapusBuku (index) {
      this.$swal.fire({
        title: 'Apakah kamu yakin?',
        icon: 'warning',
        html: `menghapus data ${this.listBuku[index]} dari daftar buku?`,
        showCancelButton: true,
        confirmButtonColor: '#3085d6',
        cancelButtonColor: '#d33',
        confirmButtonText: 'Hapus Aja'
      }).then((result) => {
        if (result.isConfirmed) {
          this.$nuxt.$emit('hapus-buku', this.listBuku[index])
          this.listBuku.splice(index, 1)
        }
      })
    }
  }
}
</script>
