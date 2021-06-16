<template>
  <div
    v-bind="$attrs"
    class="btn"
    @click="hello">
    <slot></slot>
  </div>
</template>

<script>
import { onMounted } from 'vue'

export default {
  inheritAttrs: fasle,
  props: {
    color: {
      type: String,
      default: 'gray'
    }
  },
  emits: ['hello'],
  // mounted() {
  //   console.log(this.color)
  //   console.log(this.$attrs)
  // },
  // methods: {
  //   hello() {
  //     this.$emit('hello')
  //   }
  // },
  setup(props, context) {
    // 위의 methods() 대신 composition 이용
    function hello() {
      context.emit('hello')
    }
      // 위의 mounted() 대신 composition 이용
    onMounted(() => {
      console.log(props.color)    // this. 이용 불가 => props. 로 변경
      console.log(context.attrs)  // $ 삭제 context로 대체
    })


    return {
      hello
    }
  }
}
</script>
