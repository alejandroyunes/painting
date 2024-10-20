<script setup lang="ts">
  import './contact.scss'
  import ContactForm from '~/components/organisms/form/contact/index.vue'
  //icons
  import LocationSvg from '~/components/icons/LocationSvg.vue'
  import TelephoneSvg from '~/components/icons/TelephoneSvg.vue'
  import WazeSvg from '~/components/icons/WazeSvg.vue'
  import GoogleSvg from '~/components/icons/GoogleSvg.vue'
</script>

<template>
  <div class="contact-page">

    <div class="contact-page-form">
      <h2 class="contact-form-title">{{ $t('contactWriteUs') }}</h2>
      <ContactForm />
    </div>

    <div class="contact-page-info">
      <NuxtPicture
      src="/images/contactdog.png"
      :alt="$t('billboard1Alt')"
      densities="x1"
      class="image"
      sizes="xs:400px md:400px xl:100vw" 
      format="png"
    />

    </div>

  </div>
</template>
