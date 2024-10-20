<template>
  <div>
    <div class="top-container">
      <h1>Scroll Down</h1>
      <p>Scroll down to see the sticky effect.</p>
    </div>

    <div :class="['header', { sticky: isSticky }]" ref="headerRef">
      <h2>My Header</h2>
    </div>

    <div :class="['content', { 'sticky-padding': isSticky }]">
      <h3>On Scroll Sticky Header</h3>
      <p>The header will stick to the top when you reach its scroll position.</p>
      <p>Scroll back up to remove the sticky effect.</p>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

const headerRef = ref(null);
const isSticky = ref(false);
let sticky = 0;

const checkSticky = () => {
  if (window.scrollY > sticky) {
    isSticky.value = true;
  } else {
    isSticky.value = false;
  }
};

onMounted(() => {
  if (headerRef.value) {
    sticky = headerRef.value.offsetTop;
  }
  window.addEventListener('scroll', checkSticky);
});

onUnmounted(() => {
  window.removeEventListener('scroll', checkSticky);
});
</script>

<style scoped>
body {
  margin: 0;
  font-family: Arial, Helvetica, sans-serif;
}

.top-container {
  background-color: #f1f1f1;
  padding: 30px;
  text-align: center;
}

.header {
  padding: 10px 16px;
  background: #555;
  color: #f1f1f1;
}

.content {
  padding: 16px;
}

.sticky {
  position: fixed;
  top: 0;
  width: 100%;
}

.sticky-padding {
  padding-top: 102px;
}
</style>
