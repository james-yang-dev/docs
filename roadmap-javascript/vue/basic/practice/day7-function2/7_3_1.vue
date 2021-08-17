<template>
  <div>
    <button @click="onClickType0">button type0</button>
    <button @click="onClickType1">button type1</button>
    <button @click="onClickType2">button type2</button>
    <button @click="onClickType3">button type3</button>
    <button @click="onClickType4">button type4</button>
  </div>
</template>

<script>
export default {
  name: 'app',
  data: function () {
    return {
      items: []
    }
  },
  methods: {
    onClickType0: function () {
      var url = 'https://daum.net';

      this.items.push( url );

      console.log( '현재 배열 items: ' + this.items );
    },
    onClickType1: function () {
      var url = 'https://google.com';

      this.items.push( url );

      console.log( '현재 배열 items: ' + this.items );
    },
    onClickType2: function () {
      var url = 'https://naver.com';

      this.items.push( url );

      console.log( '현재 배열 items: ' + this.items );
    },
    onClickType3: function () {
      var url = 'https://apple.com';

      this.items.push( url );

      console.log( '현재 배열 items: ' + this.items );
    },
    onClickType4: function () {
      var url = 'https://nike.com';

      this.items.push( url );

      console.log( '현재 배열 items: ' + this.items );
    }
  }
}
</script>