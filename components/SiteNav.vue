<template>
  <header>
    <nav class="shadow bg-white">
      <div class="container flex flex-row justify-between">
        <NuxtLink :to="localePath('/')">AH Hamster Love</NuxtLink>

        <div class="py-5">
          <ul class="list-none flex flex-row capitalize">
            <li class="px-8">
              <NuxtLink :to="localePath('about')">{{ $t('about') }}</NuxtLink>
            </li>
            <li class="px-8">
              <NuxtLink :to="localePath('hamsters')">{{
                $t('hamsters')
              }}</NuxtLink>
            </li>
            <li class="px-8">
              <NuxtLink :to="localePath('contact')">{{
                $t('contact')
              }}</NuxtLink>
            </li>
            <li
              v-for="locale in availableLocales"
              :key="locale.code"
              class="px-8"
            >
              <NuxtLink :to="switchLocalePath(locale.code)">{{
                locale.name
              }}</NuxtLink>
            </li>
          </ul>
        </div>
      </div>
    </nav>
  </header>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  computed: {
    availableLocales() {
      return this.$i18n?.locales
        ? this.$i18n.locales.filter(
            (i) => typeof i !== 'string' && i.code !== this.$i18n?.locale
          )
        : []
    },
  },
})
</script>
