<template>
  <h1 @click="increase">
    {{ count }} / {{ doubleCount }}
  </h1>
  <h1 @click="changeMessage">
    {{ message }} // {{ reversedMessage }}
  </h1>
</template>

<script>
// 반응성을 위해 ref를 사용해야한다.
// created 같은 경우는 setup메소드 내부에서 실행이 가능하다. lifecycle을 불러올 필요가 없다
// https://v3.ko.vuejs.org/guide/composition-api-lifecycle-hooks.html 참조
import { ref, computed, watch, onMounted } from 'vue'

export default {
  setup() {
    const count = ref(0)
    const doubleCount  = computed(() => {
      return count.value * 2
    })
    function increase() {
       // value라는 속성을 통해 데이터처럼 활용해야한다
      count.value += 1
    }

    const message = ref('Hello World!')
    const reversedMessage = computed(() => {
      return message.value.split('').reverse().join('')
    })
    watch(message, newValue => {
      console.log(newValue)
    })
    function changeMessage() {
      message.value = 'Good?!'
    }
    // created lifecycle
    console.log(message.vaule)

    onMounted(() => {
      console.log(count.value)
    })

    return {
      count,
      doubleCount,
      increase,
      message,
      reversedMessage,
      changeMessage
    }
  }
}
</script>