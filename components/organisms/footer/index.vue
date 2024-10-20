<script setup>
  import { ref } from 'vue'
  import './footer.scss'
  import InstagramSvg from '~/components/icons/social/InstagramSvg.vue'
  import WhatsAppSvg from '~/components/icons/social/WhatsAppSvg.vue'

  const currentYear = ref(new Date().getFullYear())

  const socialLinks = [
    {
      icon: InstagramSvg,
      to: 'https://www.instagram.com/',
      label: 'Visítanos en Instagram',
    },
    {
      icon: WhatsAppSvg,
      to: 'https://api.whatsapp.com/send/',
      label: 'Contáctanos por WhatsApp',
    },
  ]
</script>

<template>
  <footer class="footer">

    <div class="footer-content">
      <div class="footer-item">
        <h3 class="">Ricardo Morales Hendry</h3>
        
        <p>{{ $t('homeDescriptionStrong') }}</p>

        <div class="social-links">
          <NuxtLink v-for="link in socialLinks" :to="link.to" target="_blank">
            <component :is="link.icon" />
          </NuxtLink> 
        </div>
      </div>

      <div class="footer-item">
        <h3 class="">{{ $t('footerLinks') }}</h3>
          <ul>
            <li><NuxtLink to="/">{{ $t('home') }}</NuxtLink></li>
            <li><NuxtLink to="/home">{{ $t('gallery') }}</NuxtLink></li>
            <li><NuxtLink to="/info">{{ $t('info') }}</NuxtLink></li>
            <li><NuxtLink to="/contact">{{ $t('contact') }}</NuxtLink></li>
        </ul>
      </div>
      
      <div class="footer-item">
        <h3 class="">{{ $t('contactUs') }}</h3>
        <ul>
          <li> +1 5617145164</li>
          <li> 4406 Ringrose Dr. Missouri City, TX 77459</li>
          <li>USA.</li>
        </ul>
      </div>
    </div>

    <p class="copyright">&copy; {{ currentYear }} Ricardo Morales Hendry</p>
  </footer>
</template>
