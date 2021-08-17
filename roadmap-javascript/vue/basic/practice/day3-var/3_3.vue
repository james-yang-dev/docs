<template>
  <div>
    <button v-on:click="onClick">button sample</button>
    {{ clickCount }}
  </div>
</template>

<script>
export default {
  name: 'app',
  // data에 정의 된 변수는 컴포넌트 내에서 사용 가능하다.
  data: function () {
    return {
      clickCountGlobal: 0
    }
  },
  methods: {
    onClick: function () {
      // 지역 변수
      var clickCountLocal = 0;

      this.clickCountGlobal = this.clickCountGlobal + 1;
      clickCountLocal = clickCountLocal + 1;

      console.log( "data 변수 click count: " + this.clickCountGlobal );
      console.log( "지역 변수 click count: " + clickCountLocal );
    }
  }
}
</script>