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
            <NuxtLink to="/cart">Cart</NuxtLink>
          </ul>
        </div>
      </div>
      <h1 class="text-white font-oswald uppercase text-6xl text-center pt-24 pb-28">
        Shopping Cart
      </h1>
    </div>
    <table class="table-auto w-2/3 mt-20 mx-auto">
      <thead>
        <tr>
          <th class="text-left">Name</th>
          <th class="text-center">Price</th>
          <th class="text-right">Quantity</th>
          <th class="text-right">Total</th>
          <th>Remove</th>
        </tr>
      </thead>
      <tbody>
        <tr
          v-for="order in $store.state.orders"
          :key="order.name"
          class="font oswald uppercase text-2xl border-b"
        >
          <td class="py-10">{{ order.name }}</td>
          <td class="text-right">RM {{ order.price.toFixed(2) }}</td>
          <td class="text-center">{{ order.quantity }}</td>
          <td class="text-right">RM {{ (order.price * order.quantity).toFixed(2) }}</td>
          <td class="text-center">
            <button @click="removeItem(order.name)">❌</button>
          </td>
        </tr>
      </tbody>
      <tfoot>
        <tr class="font oswald font-bold text-2xl bg-gray-100 uppercase">
          <td class="py-10" colspan="3">Total</td>
          <td class="text-right">RM {{ total.toFixed(2) }}</td>
          <td>&nbsp;</td>
        </tr>
      </tfoot>
    </table>
  </div>
</template>

<script>
export default {
  computed: {
    total() {
      let total = 0;
      this.$store.state.orders.forEach((order) => {
        total = total + order.price * order.quantity;
      });

      return total;
    },
  },

  methods: {
    removeItem(name) {
      this.$store.commit('removeItem', name);
    },
  },
};
</script>
