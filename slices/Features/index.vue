<script setup lang="ts">
import { type Content } from "@prismicio/client";

// The array passed to `getSliceComponentProps` is purely optional.
// Consider it as a visual hint for you when templating your slice.
defineProps(
  getSliceComponentProps<Content.FeaturesSlice>([
    "slice",
    "index",
    "slices",
    "context",
  ]),
);
</script>

<template>
  <Bounded
    :data-slice-type="slice.slice_type"
    :data-slice-variation="slice.variation"
  >
    <PrismicRichText
      :field="slice.primary.heading"
      class="heading heading--md mb-12 text-center"
    />
    <div class="grid sm:grid-cols-2 lg:grid-cols-4 gap-x-8 max-w-5xl mx-auto sm:place-items-start place-items-center">
      <div 
        v-for="item in slice.items"  
        :key="item.icon ?? ''"
        class="max-w-xs grid sm:place-items-start place-items-center text-center sm:text-left mb-5"
      >
        <div
          v-if="item.icon"
          class="mb-5"
        >
          <Icon :name="item.icon" />
        </div>
        <PrismicText
          :field="item.title"
          class="heading heading--sm !font-medium pb-5"
        />
        <PrismicRichText 
          :field="item.description" 
          class="text-base text-slate-600 leading-loose" 
        />
      </div>
    </div>
  </Bounded>
</template>




  