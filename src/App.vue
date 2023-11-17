<template>
  <p>
    <!-- {{ person.name }} {{ person.age }} -->
    {{ nextYear('안녕하세요') }}
  </p>
  <p>
    <!-- <input v-bind:type="inputType" v-bind:value="inputData"> -->
    <input :type="inputType" :value="inputData">
  </p>
  <a :href="getKossieCoderLink('kossiecoder')">코지 코더 채널</a>
</template>

<script>
export default {
  name: 'App',
  data() {
      return {
        person: {
        name: '코지 코더',
        age: 34
      },
      inputValue: 'hello',
      inputType: 'text',
      aLink: 'https://www.youtube.com/'
      }
    },
  methods: {
    // 방법1
    // nextYear: function(greeting) {
    //   return (
    //     greeting + '! ' + this.person.name + '는 내년에 ' + (this.person.age + 1) + '살 입니다'
    //   );
    // },

    // 방법2
    nextYear(greeting) {
      return (
        greeting + '! ' + this.person.name + '는 내년에 ' + (this.person.age + 1) + '살 입니다'
      );
    },
    otherMethod() {
      this.nextYear();
    },
    getKossieCoderLink(channel) {
      return this.aLink + channel;
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
