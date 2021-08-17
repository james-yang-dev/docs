<template>
  <div>
    <img src="https://media.licdn.com/dms/image/C510BAQFNBMXusAxh5A/company-logo_200_200/0?e=2159024400&v=beta&t=Ujo_lU3xN_MiaOPk9030cdfIJh7r6BONYcP9_YZIvRI" />
    <img v-bind:src="url" />
    <img :src="url" />
    <button v-on:click="onClick">button sample</button>
    <button @click="onClick">button sample</button>
  </div>
</template>

<script>
export default {
  name: 'app',
  data: function () {
    return {
      url: "https://media.licdn.com/dms/image/C510BAQFNBMXusAxh5A/company-logo_200_200/0?e=2159024400&v=beta&t=Ujo_lU3xN_MiaOPk9030cdfIJh7r6BONYcP9_YZIvRI"
    }
  },
  methods: {
    onClick: function () {
      console.log( "clicked!" );
    }
  }
}
</script>