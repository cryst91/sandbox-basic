<template>
  <div>
    <ul class="list-group list-group-flush mt-3" type="buku">
      <li v-for="(pembaca, i) in listPembaca" :key="i" class="list-group-item d-flex justify-content-between align-items-center" style="padding: 0.75rem 0.25rem;">
        {{ pembaca }}
        <button class="btn btn-outline-danger rounded-pill" @click="hapusPembaca(i)">
          -
        </button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'ListPembaca',
  data () {
    return {
      listPembaca: []
    }
  },
  created () {
    this.$nuxt.$on('add-pembaca', (pembaca) => {
      this.listPembaca.push(pembaca)
    })
  },
  methods: {
    hapusPembaca (index) {
      this.$swal.fire({
        title: 'Apakah kamu yakin?',
        icon: 'warning',
        html: `menghapus data ${this.listPembaca[index]} dari daftar pembaca?`,
        showCancelButton: true,
        confirmButtonColor: '#3085d6',
        cancelButtonColor: '#d33',
        confirmButtonText: 'Hapus Aja'
      }).then((result) => {
        if (result.isConfirmed) {
          this.$nuxt.$emit('hapus-pembaca', this.listPembaca[index])
          this.listPembaca.splice(index, 1)
        }
      })
    }
  }
}
</script>
