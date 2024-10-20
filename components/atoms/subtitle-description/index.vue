<script lang="ts" setup>
import './subtitle-description.scss'

type Props = {
  title: string
  descriptionStrong?: string
  description?: string
  descriptionEnd?: string
  marginTop?: boolean
}

const { title, description, marginTop, descriptionStrong, descriptionEnd } = defineProps<Props>()

</script>

<template>
  <section class="subtitle-description">

    <h2 class="subtitle" :class="{ 'extra-top-space': marginTop }">{{ $t(title ?? '') }}</h2>

    <p class="description"><span class="strong">{{ $t(descriptionStrong ?? '') }}</span> {{ $t(description ?? '') }} <span class="end">{{ $t(descriptionEnd ?? '') }}</span></p>

  </section>
</template>
