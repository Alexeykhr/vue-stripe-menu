<template>
  <div>
    <base-title title="Full Example" />
    <pre><code
      ref="code"
      class="javascript"
    >{{ ExampleRaw }}</code></pre>
  </div>
</template>

<script>
import { onMounted, ref } from 'vue'
import highlight from 'highlight.js'
import ExampleRaw from '!!raw-loader!./ExampleRaw'
import BaseTitle from '../base/Title'

export default {
  components: {
    BaseTitle
  },
  setup() {
    const code = ref(null)

    onMounted(() => {
      highlight.highlightElement(code.value)
    })

    return { code }
  },
  data() {
    return {
      ExampleRaw
    }
  }
}
</script>
