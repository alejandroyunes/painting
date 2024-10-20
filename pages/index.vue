<script setup lang="ts">
import { useI18n } from 'vue-i18n'
import Billboard from '~/components/organisms/billboards/billboard-1/index.vue'
import SubTitle from '~/components/atoms/subtitle-description/index.vue'
import PriceTable from '~/components/organisms/table/price/index.vue'
import Billboard2 from '~/components/organisms/billboards/billboard-2/index.vue'

const { t } = useI18n()

useSeoMeta({
  title: t('homeMetaTitle'),
  description: t('homeMetaDescription'),
  ogSiteName: t('homeMetaName'),
  ogTitle: t('homeMetaTitle'),
  ogDescription: t('homeMetaDescription'),
  ogImage: '/meta/default.webp',
  ogUrl: t('homeMetaUrl'),
  ogLocale: t('siteLocale'),
  twitterTitle: t('homeMetaTitle'),
  twitterDescription: t('homeMetaDescription'),
  twitterImage: '/meta/default.webp',
  twitterCard: 'summary_large_image',
})


</script>

<template>

  <Billboard />

  <SubTitle
    marginTop
    title="homeTitle"
    description="homeDescription"
    descriptionStrong="homeDescriptionStrong"
    descriptionEnd="homeDescriptionEnd" />
    <Billboard2 
      :data="{title: 'billboard2Title', subtitle: 'billboard2Subtitle'}" />


  <SubTitle marginTop title="pricing"
    description="pricingDescription" />

    



    <PriceTable />
  


</template>
