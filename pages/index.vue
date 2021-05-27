<template>
  <div class="container">
    <div>
      <Logo />
      <h1 class="title">
        test-pwa
      </h1>
      <nuxt-link to="/about">About</nuxt-link>
    </div>

    <div class="post-items">
      <div v-for="post in posts" :key="post.id + 'post'" class="post-item">
        <h1>
          {{ post.title }}
        </h1>
        <p>
          {{ post.body }}
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      posts: []
    }
  },
  async mounted () {
    /* eslint semi: ["off"] */

    const response = await fetch('https://jsonplaceholder.typicode.com/posts')
      .then(response => response.json())
      .then(json => json);

    this.posts = response.map(item => item);
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
