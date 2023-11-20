<template>
  <div>
    <p>
      <!-- {{ person.name }} {{ person.age }} -->
      {{ nextYear('안녕하세요') }}
    </p>
    <p>
      <!-- <input v-bind:type="inputType" v-bind:value="inputValue"> -->
      <input :type="inputType" :value="inputValue">
    </p>
    <p>
      <a :href="getKossieCoderLink('kossiecoder')">코지 코더 채널</a>
    </p>
  </div>

  <hr>

  <div>
    <p>
      <button v-on:click="alert">Click me</button>
    </p>
    <p>
      {{ year }}
      <button v-on:click="plus">더하기</button>
      <button v-on:click="minus">빼기</button>
    </p>
    <div>
      <!-- v-on:submit.prevent = reload 안되게 막음 -->
      <form v-on:submit.prevent="submit"> 
        <input type="text" >
        <button type="submit">submit</button>
      </form>
    </div>
  </div>

  <hr>

  <div>
    <div>
      <!-- v-on:submit.prevent = reload 안되게 막음 -->
      <form v-on:submit.prevent="submit"> 
        <!-- <input type="text" :value="text" @keyup="updateText"> -->
        <input type="text" v-model="text" >
        <br>
        {{ text }}
        <br>
        <button type="submit">submit</button>
      </form>
    </div>
  </div>

  <hr>

  <div>
    {{ message }}
    <br>
    {{ message.split('').reverse().join('') }}
    <br>
    {{ reversedMessage }}
    <br>
    <button @click="changeMessage">click</button>
  </div>

  <hr>

  <div>
    {{ message }}
    <br>
    <button @click="changeMessage">click</button>
    <br>
    {{ updated }}
  </div>

  <hr>

  <div>
    <div :class="{ red: isRed, bold: isBold }">Hello</div>
    <button @click="update">click</button>
    <div :style="{ color: blue, fontSize: size }">Hello</div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      person: { 
        name: '코지 코더', age: 34 
      },
      inputValue: 'hello',
      inputType: 'text',
      aLink: 'https://www.youtube.com/',
      year: 2018,
      text: 'text',
      message: 'hello',
      updated: '아니오',
      isRed: false,
      isBold: false,
      blue: 'blue',
      size: '30px'
    }
  },
  methods: {
    nextYear(greeting) {
      return (
        // greeting + '! ' + this.person.name + '는 내년에 ' + (this.person.age + 1) + '살 입니다'
        `${greeting} ! ${this.person.name}는 내년에 ${this.person.age + 1}살 입니다.`
      );
    },
    otherMethod() {
      this.nextYear();
    },
    getKossieCoderLink(channel) {
      return this.aLink + channel;
    },
    alert() {
      alert('hi Kossie Coder');
    },
    plus() {
      this.year++;
    },
    minus() {
      this.year--;
    },
    submit() {
      alert("submitted");
      console.log('hello');
    },
    // updateText(event) {
    //   // console.log(event);
    //   this.text = event.target.value;
    // }
    changeMessage() {
      this.message = 'bye';
    },
    update() {
      this.isRed = !this.isRed;
      this.isBold = !this.isBold;
    }
  },
  computed: {
    reversedMessage() {
      return this.message.split('').reverse().join('');
    }
  },
  watch: {
    message(newVal, oldVal) {
      console.log('newVal : ' + newVal);
      console.log('oldVal : ' + oldVal);
      this.updated = '네';
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
.red {
  color: red;
}
.bold {
  font-weight: bold;
}
</style>
