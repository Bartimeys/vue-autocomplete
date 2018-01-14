<template>
  <div>
    <autocomplete :data="myOptions" v-model="selected"></autocomplete>
    <p v-for="i in myOptions">{{i.title}}</p>
  </div>
</template>
<script>
import Autocomplete from './Autocomplete'
export default {
  name: 'Basic',
  components: {
    Autocomplete
  },
  data () {
    return {
      myOptions: [
        {
          title: 'First Scene',
          description: 'lorem ipsum dolor amet.',
          thumbnail: 'http://lorempicsum.com/nemo/200/200/1'
        }, {
          title: 'Second Scene',
          description: 'lorem ipsum dolor amet.',
          thumbnail: 'http://lorempicsum.com/nemo/200/200/2'
        }, {
          title: 'Third Scene',
          description: 'lorem ipsum dolor amet.',
          thumbnail: 'http://lorempicsum.com/nemo/200/200/3'
        }, {
          title: 'Fourth Scene',
          description: 'lorem ipsum dolor amet.',
          thumbnail: 'http://lorempicsum.com/nemo/200/200/4'
        }
      ],
      selected: ''
    }
  }
}
</script>
