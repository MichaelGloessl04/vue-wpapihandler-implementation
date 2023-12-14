<template>
  <h1 v-html="post_title"></h1>
  <div v-html="post_content"></div>
</template>

<script>
import { WPApiHandler } from 'wpapihandler';

const url = 'https://dev.htlweiz.at/wordpress';
const headers = {
  "Content-Type": "application/json",
  "Authorization": "Basic dnVlX2pzOnJYaFcgbGg2cSB3dXV2IGQzQzUgSUtyWCBZTWtJ"
};

const wpa = new WPApiHandler(url, headers);
let connection = await wpa.get_posts(1550);

export default {
  data () {
    return {
      post_title: connection.data.title.rendered,
      post_content: connection.data.content.rendered,
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
