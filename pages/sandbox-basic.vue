<template>
  <div class="container">
    <div class="d-flex justify-content-center vh-100">
      <div class="d-flex align-items-center vw-100">
        <div class="p-3 card w-100">
          <div class="overflow-y" style="height: 70vh;">
            <div>
              <div class="text-center">
                <h1 class="mb-5">SANDBOX FRONTEND 1</h1>
              </div>
              <div class="row">
                <div class="col-md-4">
                  <InputBuku placeholderLabel="Judul Buku" />
                  <ListBuku />
                </div>
                <div class="col-md-4">
                  <InputPembaca placeholderLabel="Nama Pembaca" />
                  <ListPembaca />
                </div>
                <div class="col-md-4">
                  <div class="input-group">
                    <div style="width: 85%;">
                      <InputSelect />
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import InputBuku from '~/components/InputBuku.vue'
import InputPembaca from '~/components/InputPembaca.vue'
import InputSelect from '~/components/InputSelect.vue'
import ListBuku from '~/components/ListBuku.vue'
import ListPembaca from '~/components/ListPembaca.vue'
export default {
  name: 'SandboxBasic',
  components: { InputBuku, InputPembaca, InputSelect, ListBuku, ListPembaca }
}
</script>
