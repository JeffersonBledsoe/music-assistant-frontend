<template>
  <swiper
    :slides-per-view="panelViewItemResponsive($vuetify.display.width) + 0.5"
    :space-between="24"
    :free-mode="true"
    :navigation="mobile"
  >
    <slot></slot>
  </swiper>
</template>

<script setup lang="ts">
import { panelViewItemResponsive } from '@/helpers/utils';
import { onMounted } from 'vue';
import { useDisplay } from 'vuetify';

// TODO: Remove `mobileBreakpoint` customisation once we have removed `getBreakpointValue` and use a consistent mobile value everywhere.
const { mobile } = useDisplay({ mobileBreakpoint: 575 });

onMounted(() => {
  document.documentElement.style.setProperty(
    '--swiper-navigation-color',
    'primary',
  );
});
</script>
