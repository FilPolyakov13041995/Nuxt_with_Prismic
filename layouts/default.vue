<template>
  <div>
    <Header />
    <slot />
    <Footer />
    <div class="fixed inset-0 bg-gradient-to-tr from-emerald-50 to-cyan-50 z-[-1] opacity-50" />
  </div>
</template>

<script setup lang="ts">

const settings = useSettings()

useSeoMeta({
  title: settings.value?.data.site_title,
  description: settings.value?.data.meta_description,
  ogImage: settings.value?.data.og_image.url
})

</script>