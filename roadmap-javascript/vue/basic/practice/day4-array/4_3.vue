<template>
  <div>
    <button v-on:click="onClick">button sample</button>
    <ul>
      <li>{{ arrItem[ 0 ] }}</li>
      <li>{{ arrItem[ 1 ] }}</li>
      <li>{{ arrItem[ 2 ] }}</li>
      <li>{{ arrItem[ 3 ] }}</li>
      <li>{{ arrItem[ 4 ] }}</li>
    </ul>
    배열의 길이: {{ arrItem.length }}
  </div>
</template>

<script>
export default {
  name: 'app',
  data: function () {
    return {
      arrItem: [ "sample item1", "sample item2", "sample item3", "sample item4", "sample item5" ]
    }
  },
  methods: {
    onClick: function () {
      this.arrItem.push( "sample item added" );

      console.log( "list 길이: " + this.arrItem.length );
    }
  }
}
</script>