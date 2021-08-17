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
      arrItem: []
    }
  },
  methods: {
    addItem( url ) {
      this.arrItem.push( url );

      console.log( "현재 배열 items: " + this.arrItem );
    },
    onClickType0: function () {
      this.addItem( "https://daum.net" );
    },
    onClickType1: function () {
      this.addItem( "https://google.com" );
    },
    onClickType2: function () {
      this.addItem( "https://naver.com" );
    },
    onClickType3: function () {
      this.addItem( "https://apple.com" );
    },
    onClickType4: function () {
      this.addItem( "https://nike.com" );
    }
  }
}
</script>