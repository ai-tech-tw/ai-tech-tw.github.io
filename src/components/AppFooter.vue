<template>
  <footer class="mt-16 pb-16 text-sm leading-6">
    <div class="max-w-7xl mx-auto mt-5 divide-y divide-gray-200 px-4 sm:px-6 md:px-8 text-sky-700">
      <a class="mr-3" href="https://github.com/ai-tech-tw/ai-tech-tw.github.io">網站原始碼</a>
      <a class="mr-3" href="https://web-tech-tw.github.io/#/privacy">隱私權政策</a>
    </div>
    <div class="max-w-7xl mx-auto mt-5 divide-y divide-gray-200 px-4 sm:px-6 md:px-8">
      &copy; {{year}} 臺灣網際網路技術推廣組織 Taiwan Web Technology Promotion Organization (Web Tech TW)
    </div>
  </footer>
</template>

<script setup>
const year = new Date().getFullYear();
</script>
