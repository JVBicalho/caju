<template>
  <div class="container">
    <img alt="Vue logo" src="../assets/logo.png">
    <CaJu />
  </div>
</template>

<script>
// @ is an alias to /src

import CaJu from '@/components/CaJu.vue'

export default {
  name: 'Home',
  components: {
   CaJu
  }
}
</script>
