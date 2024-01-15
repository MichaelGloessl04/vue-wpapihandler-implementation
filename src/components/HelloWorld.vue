<template>
  <div class="container">
    <h1>{{ post_title }}</h1>
    <div class="post-content" v-html="post_content"></div>
  </div>
</template>

<script>
  import { WPApiHandler } from 'wpapihandler';

  const url = 'https://dev.htlweiz.at/wordpress';
  const headers = {
    "Content-Type": "application/json",
    "Authorization": "Basic d3BhcGloYW5kbGVyOm1vZ2tpOC1zYXp2eWotaHVjcVVi"
  };

  const wpa = new WPApiHandler(url, headers);
  let post = await wpa.get_posts('1910');

  console.log(post)

  export default {
    data () {
      return {
        post_title: post[0].title,
        post_content: post[0].content,
      }
   }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container {
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
}

h1 {
  font-size: 24px;
  font-weight: bold;
  color: #333;
  margin-bottom: 10px;
}

.post-content {
  font-size: 16px;
  line-height: 1.5;
  color: #666;
}

.post-content p {
  margin-bottom: 10px;
}

.post-content a {
  color: #007bff;
  text-decoration: none;
}

.post-content a:hover {
  text-decoration: underline;
}

.post-content img {
  max-width: 100%;
  height: auto;
  margin-bottom: 10px;
}

/* Add CSS to adjust list style */
.post-content ul {
  list-style-position: inside;
}
</style>
