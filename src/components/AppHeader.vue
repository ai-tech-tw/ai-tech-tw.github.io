<template>
  <div class="app-header">
    <div class="max-w-7xl mx-auto px-4 sm:px-6">
      <div class="flex justify-between items-center border-b-2 border-gray-100 py-6 md:justify-start md:space-x-10">
        <div class="flex justify-start lg:w-0 lg:flex-1">
          <router-link to="/">
            <h1 class="flex-auto text-lg font-semibold text-gray-900 hidden sm:block">
              {{ titleLong }}
            </h1>
            <h1 class="flex-auto text-lg font-semibold text-gray-900 sm:hidden">
              {{ titleShort }}
            </h1>
            <p class="flex-auto text-md font-normal text-gray-500 hidden sm:block">
              {{ subtitleLong }}
            </p>
            <p class="flex-auto text-sm font-normal text-gray-500 sm:hidden">
              {{ subtitleShort }}
            </p>
          </router-link>
        </div>
        <app-header-normal />
        <app-header-mobile-icon-button class="-mr-2 -my-2 md:hidden" @click="handleMobileMenuBtnOpenClick">
          <bars4-icon class="h-6 w-6" />
        </app-header-mobile-icon-button>
      </div>
    </div>
    <app-header-mobile v-show="isMobileMenuOpened" @close="handleMobileMenuBtnCloseClick" />
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted, provide } from "vue";

import { Bars4Icon } from "@heroicons/vue/24/solid"

import {
  titleLong,
  titleShort,
  subtitleLong,
  subtitleShort,
} from "./AppHeaderMenuData.js";

import AppHeaderNormal from "./AppHeaderNormal.vue";
import AppHeaderMobile from "./AppHeaderMobile.vue";

import AppHeaderMobileIconButton from "./AppHeaderMobileIconButton.vue";

const isMobileMenuOpened = ref(false);

const parentMenuState = ref(true);
provide('parent-menu-state', parentMenuState);

const handleMobileMenuBtnOpenClick = () => {
  isMobileMenuOpened.value = true;
  parentMenuState.value = true;
}

const handleMobileMenuBtnCloseClick = () => {
  isMobileMenuOpened.value = false;
  parentMenuState.value = false;
}

const handleDocumentClick = (e) => {
  if (!document.querySelector('.app-header').contains(e.target)) {
    parentMenuState.value = false;
  }
};

onMounted(() => {
  document.addEventListener('click', handleDocumentClick);
});

onUnmounted(() => {
  document.removeEventListener('click', handleDocumentClick);
});
</script>
