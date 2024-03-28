<template>
  <section class="container-fluid">
    <div class="row">
      <div class="col-4">
        <h4>What you wanna watch boi</h4>
        <form @submit.prevent="letsWatch()" action="">
          <div class="d-flex">
            <input v-model="watchLink" type="text">
            <button class="btn btn-outline-dark ms-3">Send it</button>
          </div>
        </form>
      </div>
    </div>
    <div class="row">
      <div class="col-10">
        <iframe :src="finalLink" width="700px" height="500px"></iframe>
      </div>
    </div>
  </section>
  </template>
  
  <script>
  import { ref } from 'vue';
  import Pop from '../utils/Pop';
  
  export default {
    setup() {
      let watchLink = ref('')
      let finalLink = ref('')
      async function letsWatch(){
        let length = watchLink.value.length
        let link = watchLink.value.slice(0, 24)
        let linkTwo = watchLink.value.slice(32, length)
        let draftLink = link += 'embed/'
        let videoLink = draftLink += linkTwo
        finalLink.value = videoLink
        watchLink.value = ''
        Pop.success("OH YEAH BROTHER")
      }
      return {
        finalLink,
        watchLink,
        letsWatch
      }
    }
  }
  </script>
  
  <style scoped lang="scss">
  .home {
    display: grid;
    height: 80vh;
    place-content: center;
    text-align: center;
    user-select: none;
  
    .home-card {
      width: clamp(500px, 50vw, 100%);
  
      >img {
        height: 200px;
        max-width: 200px;
        width: 100%;
        object-fit: contain;
        object-position: center;
      }
    }
  }
  </style>
