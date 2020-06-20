<template>
  <div class="container">
    <img alt="Vue logo" src="../assets/logo.png" style="filter: drop-shadow(0px 0px 10px rgba(0,0,0,.5));">
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
