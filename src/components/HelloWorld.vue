<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div>{{ computedTest }}</div>
    <div>{{ test }}</div>
  </div>
</template>

<script lang="ts">
import {
  defineComponent,
  ref,
  onMounted,
  onUpdated,
  onUnmounted,
  getCurrentInstance,
  computed
} from 'vue'
import { mapState, useStore } from 'vuex'

export default defineComponent({
  name: 'HelloWorld',
  props: {
    msg: String
  },
  setup (props: {msg?: string}) {
    const instance = getCurrentInstance()
    console.log(instance)
    const store = useStore()
    console.log(store)
    const count = ref(0)

    const computedTest = computed(() => store.state.test)
    // if (typeof ctx.root === 'object') {

    // }
    // const store = root.$store
    // const router = root.$router

    const increase = (): void => {
      count.value++
    }
    function test (x: number): string {
      return props.toString() + x
    }
    test(1)
    // test('number');
    // 生命周期
    onMounted(() => {
      console.log('mounted vue3 typescript')
    })
    onUpdated(() => {
      console.log('updated vue3 typescript')
    })
    onUnmounted(() => {
      console.log('onUnmounted vue3 typescript')
    })
    const map = mapState(['test'])
    console.log(map)
    console.log(map.test())
    // 暴露给模板
    return {
      // test: computed(map.test),
      computedTest,
      count,
      increase
    }
  }
})
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
