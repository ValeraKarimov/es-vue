<template>
  <div id="App">
    <h1> {{ firstName }}</h1>
    <h2> {{ num*2 }}</h2>
    <h3> {{ num > 1 ? 'Num > 1' : 'Num smaller less 1' }}</h3>
    <h3> {{ obj.age}}</h3>
    <a :href="linkUrl">Link to google</a>

    <template v-if="msgIsVisible === 1"><div class="message">Some message!</div></template>
    <template v-else-if="msgIsVisible === 2"><div class="message">second message!</div></template>
    <template v-else><div class="message">Another message!</div></template>

    <div v-show="isVisibleBlock">V show example</div>

    <div class="name-input" v-if="inputNameVisible">
      <label>Name</label>
      <input type="text" placeholder="input name" key="name-input">
    </div>

    <div class="nickname-input" v-else>
      <label>NickName</label>
      <input type="text" placeholder="input nickname" key="nickname-input">
    </div>

<button @click="inputNameVisible = !inputNameVisible">Change Form</button>

<button @click.right="(onClik('some value', $event))">Click event</button>

<a href="" @click.prevent="onLinkClick">Link</a>

<h1>{{ text }}</h1>

<input type="text" @keyup.enter="onKeyUp" />

<ul>
  <li v-for="(color, index) in colors" :key="index"> {{ index + 1}} {{ color }}</li>
  <li v-for="user in users" :key="user.id">{{ user.name }} : {{ user.age }}</li>
  <li v-for="(value, name, index) in product" :key="index" >
    {{ index }}) {{ name }} : {{ value }}</li>
    <div>
      <input type="text" @keyup.enter="addNewColor">
      <input type="text" @keyup.enter="deleteProp">
    </div>
</ul>

  </div>
</template>

<script>
export default {
  name: 'App',
  components: {
  },
  data: () => ({
    text: '',
    firstName: 'Valerii',
    num: 2,
    obj: {
      age: 30,
    },
    linkUrl: 'https://google.com',
    msgIsVisible: 1,
    isVisibleBlock: true,
    inputNameVisible: true,
    colors: ['orange', 'red', 'blue', 'black'],
    users: [{ name: 'Valerii', age: '26', id: '1' }, { name: 'Denis', age: '30', id: '2' }],
    product: {
      brand: 'Apple',
      model: 'Iphone 11 Pro',
      price: '$1000',
    },
  }),
  methods: {
    onClik(value, e) {
      console.log(value, e);
    },
    onLinkClick() {
      console.log('Link Click');
    },
    onKeyUp(e) {
      console.log(e);
      this.text = e.target.value;
    },
    addNewColor(e) {
      this.colors.push(e.target.value);
      console.log(this);
    },
    deleteProp(e) {
      this.delete.product(this.product, e.target.value);
      console.log(this.product);
    },
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
