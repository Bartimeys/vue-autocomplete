<template>
  <div>
    <autocomplete :data="myOptions" v-model="selected"></autocomplete>
    <section v-for="i in myOptions" v-bind:key="i.title">
      <ul>
        <li>{{i.title}}</li>
        <li><img :src="i.thumbnail" :alt="i.title"/></li>
        <li>{{i.description}}</li>
      </ul>
    </section>
  </div>
</template>
<script>
import Autocomplete from './Autocomplete/Autocomplete'
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
