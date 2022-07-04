<template>
  <div>
    <p>Hello from child component</p>
    <input type="text" @input="$emit('inputMessage', $event.target.value)"  @change="sendMessage">
  </div>
</template>

<script>
export default {
    emits: {
        messageChange: null,
        inputMessage: null
    },
    props: {
        height: Number,
        age: {
            type: Number,
            default: 0,
            required: true,
            validator: (value) => {
                return value >= 0
            }
        }
    },
    methods: {
        sendMessage(event) {
            this.$emit('messageChange', event.target.value)
        }
    }
}
</script>

<style>

</style>