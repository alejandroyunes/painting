<script setup lang="ts">
import './floating-whatapp.scss'
import WhatsappSvg from '~/components/icons/social/WhatsAppSvg.vue'

const handleClick = () => {
}
</script>

<template>
  <div class="floating-whatapp">
      <NuxtLink to="https://api.whatsapp.com/">  
        <WhatsappSvg />
      </NuxtLink>
  </div>
</template>