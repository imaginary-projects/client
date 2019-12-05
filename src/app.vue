<template>
  <div>
    <h1>{{ message }}</h1>
  </div>
</template>

<script>
export default {
  data() {
    return {
      file : '',
      message: 'Hello world',
    };
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