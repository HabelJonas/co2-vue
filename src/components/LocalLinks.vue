<template>
    <div class="local-links">
        <ul>
            <li><a @click.prevent="scrollToTop" href="#">Zum Anfang</a></li>
            <li><a @click.prevent="scrollToBottom" href="#">Zum Ende</a></li>
        </ul>
    </div>
</template>
  
<script>
export default {
    name: 'LocalLinks',
    methods: {
        scrollToTop() {
            window.scrollTo({
                top: 0,
                behavior: 'smooth'
            });
        },
        scrollToBottom() {
            window.scrollTo({
                top: document.body.scrollHeight,
                behavior: 'smooth'
            });
        }
    }
}
</script>
  
<style>
.local-links {
  position: fixed;
  z-index: 9999;
}

.local-links ul {
  list-style: none;
  margin: 0;
  padding: 0;
}

.local-links li {
  display: block;
  margin-bottom: 10px;
}

.local-links a {
  display: block;
  font-size: 14px;
  color: #555;
  text-decoration: none;
}

.local-links a:hover {
  color: #000;
}
</style>
  
  