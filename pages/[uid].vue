<script setup lang="ts">
import { components } from '~/slices'

const prismic = usePrismic()
const route = useRoute()
const { data: page } = useAsyncData(route.params.uid as string, () =>
  prismic.client.getByUID('page', route.params.uid as string, {
    fetchLinks: [
      'testimonial.quote',
      'testimonial.avatar',
      'testimonial.name',
      'testimonial.job_title'
    ]
  })
)

useSeoMeta({
  title: page.value?.data.meta_title ?? undefined,
  description: page.value?.data.meta_description ?? undefined,
  ogImage: page.value?.data.meta_image.url ?? undefined
})
</script>


<template>
  <SliceZone
    wrapper="main"
    :slices="page?.data.slices ?? []"
    :components="components"
  />
</template>
