<template>
  <div class="container">
    <div>
      <h1 class="title">
        ABOUT
      </h1>
      <nuxt-link to="/">Main</nuxt-link>
    </div>

    <div class="post-items">
      <div v-for="photo in photos" :key="photo.id + 'post'" class="post-item">
        <h1>
          {{ photo.title }}
        </h1>

        <img :src="photo.url" alt="photo" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      photos: []
    }
  },
  async mounted () {
    /* eslint semi: ["off"] */

    const response = await fetch('https://jsonplaceholder.typicode.com/albums/1/photos')
      .then(response => response.json())
      .then(json => json);

    this.photos = response.map(item => item);
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  padding: 0 20px;
  min-height: 100vh;
  /* display: flex; */
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.post-items {
  margin-top: 20px;
}

.post-item {
  border: 1px solid gray;
  margin-bottom: 10px;
}
</style>
