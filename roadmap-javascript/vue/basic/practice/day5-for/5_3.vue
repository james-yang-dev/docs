<template>
  <div>
    <button v-on:click="onClick">button sample</button>
    <ul>
      <!-- value: 배열 각 아이템의 값, index: 배열의 순번, 유일한 값을 key 값으로 주는 게 규칙 -->
      <!-- 일단 배우지 않은 v-bind:key 부분은 넘어간다. -->
      <li v-for="(item, index) in arrItem" v-bind:key="index">{{ item }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'app',
  data: function () {
    return {
      arrItem: [ "sample item 1", "sample item 2", "sample item 3", "sample item 4", "sample item 5" ]
    }
  },
  methods: {
    onClick: function () {
      this.arrItem.push( 'sample added' );
    }
  }
}
</script>