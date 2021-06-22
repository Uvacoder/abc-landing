<template>
  <div class="min-h-screen min-w-screen bg-custombg">
      <HeaderLauncher v-if="$route.name.includes('launcher')"/>
      <HeaderDefault v-else />
    <Nuxt />
    <FooterLauncher v-if="$route.name.includes('launcher')" />
    <Footer v-else/>
  </div>
</template>

<style>

</style>
