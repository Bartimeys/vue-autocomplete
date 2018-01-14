<template>
  <div>

    <input :placeholder="placeholder" class="autocomplete" v-model="typed" @blur="verificaBlur($event)">
    <ul class="autocompleteList" v-if="showResult">
      <li v-if="noneFind" id="autocompleteNoResult">{{ noresults }}</li>
      <li class="autocompleteItemsList" v-for="result in results" @click="select(result)">{{ result }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    value: {
      default: null
    },
    data: {
      type: Array,
      required: true
    },
    minlength: {
      type: Number,
      default: 3
    },
    noresults: {
      type: String,
      default: 'No matching results'
    },
    placeholder: {
      type: String,
      default: null
    }
  },
  data () {
    return {
      typed: '',
      showResult: false,
      noneFind: false,
      results: ''
    }
  },
  watch: {
    typed () {
      if (this.typed.length >= this.minlength) {
        let verifier = this.typed
        let mapVerify = this.data.map(x => x.title)
        let verify = mapVerify.filter(function (elem) {
          return elem === verifier
        })
        if (verify.length === 0) {
          this.filterData()
        }
      }
      if (this.typed.length < this.minlength) {
        this.showResult = false
        this.results = ''
      }
    }
  },
  methods: {
    filterData () {
      let reg = new RegExp(this.typed.split('').join('\\w*').replace(/\W/, ''), 'i')
      let map = this.data.map(x => x.title)
      let result = map.filter(function (elem) {
        if (elem.match(reg)) {
          return elem
        }
      })
      this.results = result
      this.showResult = true
      if (result.length === 0) {
        this.noneFind = true
      } else {
        this.noneFind = false
      }
    },
    select (result) {
      this.typed = result
      this.$emit('input', this.typed)
      this.showResult = false
    },
    verificaBlur (event) {
      let self = this
      setTimeout(function () {
        let verificador = self.typed
        let mapBlur = self.data.map(x => x.title)
        let verify = mapBlur.filter(function (elem) {
          return elem === verificador
        })
        if (verify.length === 0) {
          self.typed = ''
          self.$emit('input', self.typed)
        }
      }, 260)
    }
  }
}
</script>
<style lang="css">
@import 'autocomplete.css';
</style>
