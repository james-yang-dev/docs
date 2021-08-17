<template>
  <div>
    <button v-on:click="onClick">button sample</button>
  </div>
</template>

<script>
export default {
  name: 'app',
  methods: {
    onClick: function () {
      console.log( 'click count: 1' );
    }
  }
}
</script>