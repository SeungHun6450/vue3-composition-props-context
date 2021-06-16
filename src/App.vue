<!-- Composition -->
<!--
<template>
  <h1 @click="increase">
    {{ count }} / {{ doubleCount }}
  </h1>
  <h1 @click="changeMessage">
    {{ message }} // {{ reversedMessage }}
  </h1>
</template>

<script>
export default {
  data() {
    return {
      count: 0,
      message: 'Hello world!'
    }
  },
  computed: {
    doubleCount() {
      return this.count * 2
    },
    reversedMessage() {
      return this.message.split('').reverse().join('')
    }
  },
  watch: {
    message(newValue) {
      console.log(newValue)
    }
  },
  created() {
    console.log(this.message)
  },
  mounted() {
    console.log(this.count)
  },
  methods: {
    increase() {
      this.count += 1
    },
    changeMessage() {
      this.message = 'Good?!'
    }
  }
}
</script>
-->


<!-- props, context -->
<template>
  <MyBtn
    class="heropy"
    style="color:red;"
    color="#ff0000"
    @hello="log">
    Apple
  </MyBtn>
</template>

<script>
import MyBtn from '~/components/MyBtn'

export default {
  components: {
    MyBtn
  },
  methods: {
    log() {
      console.log('Hello world!')
    }
  }
}
</script>
