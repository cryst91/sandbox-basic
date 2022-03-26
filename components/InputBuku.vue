<template>
  <div class="input-group ">
    <input v-model="inputData" type="text" :placeholder="placeholderLabel" class="form-control rounded-pill" style="height: 50px;">
    <div class="input-group-append">
      <button type="button" class="btn btn-outline-primary rounded-pill ml-3" style="width: 50px;" @click="addBuku();">
        +
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'InputBuku',
  data () {
    return {
      inputData: ''
    }
  },
  props: {
    placeholderLabel: {
      type: String,
      required: false
    }
  },
  methods: {
    addBuku () {
      this.$nuxt.$emit('add-buku', this.inputData)
    }
  }
}
</script>
