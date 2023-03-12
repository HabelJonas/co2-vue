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
   display: flex;
   justify-content: space-between;
   width: 200px;
   padding: 10px;
   margin-top: 10px;
   background-color: #F7B1AB;
   border-radius: 10px;
   box-shadow: 0 2px 5px rgba(0, 0, 0, 0.3);
   z-index: 9999;
}

@media (max-width: 767px) {
   .local-links {
      bottom: 0;
      left: 0;
      width: 99%;
      padding: 5px;
      justify-content: center;
   }
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
  
  