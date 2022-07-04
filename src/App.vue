<script>
import ChildComponent from './components/ChildComponent.vue'

export default {
  components: {
    ChildComponent
  },
  data: () => ({
    name: 'Christian',
    a: 1,
    items: [ 1, 2, 3, 4, 6],
    item: null,
    message: 'no message',
    otherMessage: null
  }),
  created() {
    this.items[0] = 5
  },
  computed: {
    double() { return this.a * 2 },
    triple: (i) => i.a * 3,
    value: {
      get () { return this.name },
      set (v) { this.name = v }
    }
  },
  watch: {
    value(data, old) {
      console.log(`[watch] - ${data} - ${old}`)
    },
    items: {
      handler(val) {
        // deep: true watches nested values
        console.log(`[watch][value1] - ${val}`)
      },
      deep: true
    }
  },
  methods: {
    change(data) {
      this.message = data
    }
  }
}
</script>

<template>
  <div>
    <p>Hello there. {{ name }}</p>
    <child-component :height="2" :age="24" @message-change="change" @input-message="otherMessage = $event"></child-component>
    <p>Pre-message: {{ otherMessage }}</p>
    <p>Final Message: {{ message }}</p>
  </div>
</template>

<style>
</style>
