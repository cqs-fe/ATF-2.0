<template>
    <div id="aut">
       <headerGuide></headerGuide>
       <sidebar></sidebar>
       <copyright></copyright>
    </div>
</template>

<script>
import headerGuide from 'components/header-guide.vue'
import sidebar from 'components/sidebar.vue'
import copyright from 'components/copyright.vue'
export default {
  name: 'aut',
  components: { headerGuide, sidebar, copyright }
}
</script>

<style>
  @import '../../assets/css/base.scss';
</style>
