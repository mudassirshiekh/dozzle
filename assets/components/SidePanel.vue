<template>
  <aside class="fixed h-screen w-[inherit] overflow-auto p-3" data-testid="navigation">
    <h1>
      <router-link :to="{ name: '/' }">
        <LogoWithText class="logo h-16 w-40" />
      </router-link>

      <small class="font-weight-light mb-4 block text-xs" v-if="hostname">
        {{ hostname }}
      </small>
    </h1>

    <button
      class="input input-sm hover:border-primary mt-4 inline-flex cursor-pointer items-center gap-2 font-light"
      @click="$emit('search')"
      :title="$t('tooltip.search')"
      data-testid="search"
    >
      <mdi:magnify />
      {{ $t("placeholder.search") }}
      <key-shortcut char="k" class="text-base-content/70"></key-shortcut>
    </button>

    <side-menu class="mt-4"></side-menu>
  </aside>
</template>

<script lang="ts" setup>
import LogoWithText from "@/logo-text.svg";
const { hostname } = config;
</script>

<style scoped lang="postcss">
.logo {
  :deep(.content-fill) {
    @apply fill-base-content;
  }

  :deep(.secondary-fill) {
    @apply fill-secondary;
  }
}
</style>
