<template>
  <div class="about">
    <h1>This is an about page</h1>
    <input type="file"  @change="upload($event)" id="file-input">
    <button type="button" @click="veiwFile">do</button>
    <p>{{ result }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      result: '',
      file: '',
    }
  },

  mounted() {
    
  },
  methods: {
    upload(e){
      // let data = new FormData();
      this.file = e.target.files[0];
    },
    veiwFile(){
      let reader = new FileReader();
  
      reader.readAsArrayBuffer(this.file);
  
      reader.onload = function() {
        let view = new Uint16Array(reader.result);
        console.log(view);
  
      };
  
      reader.onerror = function() {
        console.log(reader.error);
      };
    },
  }
}
</script>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
