<script setup lang="ts">
import './header.scss'
import { ref, onMounted, onUnmounted, computed, inject } from 'vue'
import { useI18n } from 'vue-i18n'
import UseSetTheme from '~/components/hooks/useSetTheme.vue'
import SliderTopNav from '~/components/organisms/menus/sliders/top-nav/index.vue'
import Dropdown from '~/components/organisms/menus/dropdown/desktop/index.vue'

import Button from '~/components/atoms/buttons/default/index.vue'
import HamburgerSvg from '~/components/icons/header/HamburgerSvg.vue'

const headerRef = ref<HTMLElement | null>(null)
const topContainerRef = ref<HTMLElement | null>(null)
const isSticky = ref(false)
const headerHeight = ref(0)
const topContainerHeight = ref(0)
const totalHeaderHeight = computed(() => headerHeight.value + topContainerHeight.value)

const isSliderTopNavOpen = ref<boolean | undefined>(undefined)


const updateHeights = () => {
  if (headerRef.value) {
    headerHeight.value = headerRef.value.offsetHeight
  }
  if (topContainerRef.value) {
    topContainerHeight.value = topContainerRef.value.offsetHeight
  }
}

const checkSticky = () => {
  if (topContainerRef.value) {
    isSticky.value = window.scrollY > topContainerRef.value.offsetHeight
  }
}

onMounted(() => {
  updateHeights()
  window.addEventListener('scroll', checkSticky)
  window.addEventListener('resize', updateHeights)
  // Use MutationObserver to detect changes in the DOM
  const observer = new MutationObserver(updateHeights)
  observer.observe(document.body, { childList: true, subtree: true })
})

onUnmounted(() => {
  window.removeEventListener('scroll', checkSticky)
  window.removeEventListener('resize', updateHeights)
})

const toggleSliderTopNav = () => {
  isSliderTopNavOpen.value = !isSliderTopNavOpen.value
}

const { locale } = useI18n({ useScope: 'global' })
const config = inject(Symbol.for('FormKitConfig')) as { locale: string } | undefined

const setLanguage = (language: string) => {
  locale.value = language

  if (config !== undefined) {
    config.locale = language
  }
}

</script>

<template>

  <div class="sticky-header-container" :style="{ height: `${totalHeaderHeight}px` }">

    <div ref="topContainerRef" class="sticky-header-top" :class="{ 'sticky-header-invisible': isSticky }">

      <div class="sticky-header-item">
        <h1>PetnPaw</h1>
        <NuxtPicture src="/images/petnpaw-dog.png" alt="Logo Dr. Puerta" class="logo" sizes="xs:110px md:110px xl:110px"
          format="png" @load="updateHeights" />
        <h1>Oil portraits</h1>
      </div>

      <span>Custom pet painted portraits by</span>
      <p>Ricardo Morales Hendry</p>

    </div>

    <div ref="headerRef" class="sticky-header" :class="{ 'sticky': isSticky }">

      <Dropdown class="desktop-only" />

      <UseSetTheme class="dark-mode-icons" />

      <div class="language-switcher">
        <button :class="{ 'active': locale === 'en' }" @click="setLanguage('en')">en</button>
        <button :class="{ 'active': locale === 'es' }" @click="setLanguage('es')">es</button>
      </div>
      

      <div class="hamburger-menu mobile-only" @click="toggleSliderTopNav">
        <HamburgerSvg class="icon" aria-label="Abrir menú de navegación" />
      </div>

      <SliderTopNav :toggle="toggleSliderTopNav" :isOpen="isSliderTopNavOpen" />
    </div>

  </div>
</template>