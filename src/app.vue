<template>
  <div>
    <mainpage></mainpage>
  </div>
</template>

<script>

import mainpage from './views/mainPage'

export default {
  data() {
    return {

    };
  },
  components:{
      mainpage
    },
  methods : {
    submit(){
      let formData = new FormData
      formData.append('file',this.file)

    },
    fileHandler(){
      console.log('change on')
      this.file = this.$$refs.file.files[0]
    }
  }
};
</script>

<style scoped>
</style>