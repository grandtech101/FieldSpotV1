<template>
  <div>
    <div class="bg-[url('/features-page.jpg')]">
      <div id="Features" class="grid grid-cols-2 py-5">
        <div id="features-left">
          <img src="logo.png" class="w-[150px]" alt="" />
        </div>

        <div id="features-right">
          <ul class="grid grid-cols-5 text-2xl font-oswald text-white pt-5">
            <li>Home</li>
            <NuxtLink to="/menu">Features</NuxtLink>
            <li>Solutions</li>
            <li>Contacts</li>
          </ul>
        </div>
      </div>
      <h1 class="text-white font-oswald uppercase text-6xl text-center pt-24 pb-28">
        Our Features
      </h1>
    </div>
    <div id="items" class="grid grid-cols-3">
      <FeatureItem v-for="b in items" :key="b.name" :item="b" />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [],
    };
  },
  mounted() {
    this.$axios.get('items.json').then((response) => {
      this.items = response.data.FieldSpot;
    });
  },
};
</script>
