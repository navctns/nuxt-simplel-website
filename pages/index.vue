<template>
  <div>
    <the-navbar>
      <template #logo>
        <img src="../assets/web/logo/logo-simple.png" alt="">
      </template>
    </the-navbar>
    <Tutorial/>
  </div>
</template>

<script>
import TheNavbar from '../components/TheNavbar'

export default {
  name: 'IndexPage',
  components: {TheNavbar}
}
</script>
