<template>
  <div>
    <autocomplete :data="myOptions" v-model="selected"></autocomplete>
    <ul class="list">
      <li v-for="i in myOptions" v-bind:key="i.title" v-if="i.title === selected ">
          <a href="#"><img :src="i.thumbnail" :alt="i.title"/>
          <h1>{{i.title}}</h1>
          <p>{{i.description}}</p>
        </a>
      </li>
      <li v-for="i in myOptions" v-bind:key="i.title" class="list" v-show="selected === ''">
      <a href="#"><img :src="i.thumbnail" :alt="i.title"/>
        <h1>{{i.title}}</h1>
        <p>{{i.description}}</p>
      </a>
    </li>
    </ul>
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
          title: 'First Scene 2',
          description: 'lorem ipsum dolor amet.',
          thumbnail: 'http://lorempicsum.com/nemo/200/200/1'
        }, {
          title: 'Second Scene',
          description: 'lorem ipsum dolor amet.',
          thumbnail: 'http://lorempicsum.com/nemo/200/200/2'
        }, {
          title: 'Second Scene 2',
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
  },
  methods: {
    filterByName: function () {
      let result = this.myOptions.filter(o => o.title === this.selected)
      return result
    }
  }
}
</script>
<style lang="css">
  @import 'style.css';
</style>
