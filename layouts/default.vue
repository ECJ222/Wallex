<template>
  <div class="layout w-full flex">
    <Sidebar />
    <MobileHeader />
    <Nuxt />
  </div>
</template>

<script>
export default {
  name: 'DashboardLayout',
}
</script>

<style lang="scss">
.layout {
  height: 100vh;
  flex-direction: column;
  overflow-y: auto;
  overflow-x: hidden;

  @include respond-to('min-lg') {
    padding: $font-lg 0;
    flex-direction: row;
  }
}

@include respond-to('min-lg') {
  ::-webkit-scrollbar {
    width: 4px;
    height: 2px;
  }

  ::-webkit-scrollbar-track {
    border-radius: 24px;
  }

  ::-webkit-scrollbar-thumb {
    width: 2px;
    background-color: #d6d6d6;
    border-radius: 24px;
    -webkit-border-radius: 24px;
    -moz-border-radius: 24px;
    -ms-border-radius: 24px;
    -o-border-radius: 24px;
  }
}
</style>
