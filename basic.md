# vue js

## data binding

```js
var app = new Vue({
  el: "#app",
  data: {
    message: "Hello Vue!",
    imgUrl: "./img/image.jpg",
  },
});
```

### data binding

> syntax:

```html
<div>{{ [Vue data] }}</div>
```

```html
<div id="app">
  <p>{{ message }}</p>
</div>
```

### attribute binding

> syntax:

```html
<div v-bind:[attribute]="[Vue data]"></div>
```

```html
<div id="app">
  <img v-bind:src="imgUrl" />
</div>
```

### v-if

> syntax:

```html
<div v-if="[Vue data]"></div>
```

```html
<div id="app">
  <div v-if="message">message is true</div>
  <div v-else>message is false</div>
</div>
```

```jsx
  const app = Vue.createApp({
   data() {
    return {
      typewritersInStock: true,
      typewriterCount: 4
    }
   }
  })

  // html
  <p v-if="typewritersInStock">in stock</p>
  <p v-else>not in stock</p>
```

```jsx
<p v-if="typewriterCount>3">
  In stock
</p>

<p v-else-if="typewriterCount>0">
  Very few left!
</p>

<p v-else>
  Not in stock
</p>
```

### v-show

> syntax:

```html
<div v-show="[Vue data]"></div>
```

```html
<div id="app">
  <div v-show="message">message is true</div>
  <div v-show="!message">message is false</div>
</div>
```

### v-for

> syntax:

```html
<div :key="{{Vue-data.id}}" v-for="[Vue-data] in [Vue-AllData]"></div>
```

```html
<div id="app">
  <div v-for="(item,index) in items" :key="item.id">
    {{index}}:{{ item.message }} <br />
  </div>
</div>

<script>
  var app = new Vue({
    el: "#app",
    data: {
      items: [
        { id: 1, message: "Foo" },
        { id: 2, message: "Bar" },
      ],
    },
  });
</script>

// output: // 0:Foo // 1:Bar
```

### v-on

> syntax:

```html
<div v-on:[event]="[Vue method]"></div>
```

```html
<div id="app">
  <button @:click="mobileNav = !mobileNav">nav</button>
  <button v-on:click="count++">count</button>
  <p>{{ count }}</p>
</div>

<script>
  var app = new Vue({
    el: "#app",
    data: {
      count: 0,
      mobileNav: false,
    },
  });
</script>
```

### methods

> syntax:

```js
var app = new Vue({
  el: "#app",
  data: {
    message: "Hello Vue!",
  },
  methods: {
    [Vue method]: function () {
      // code
    },
  },
});
```

```jsx
const app = Vue.createApp({
  data() {
    return {
      text: "",
    };
  },
  methods: {
    writeText(text) {
      this.text = text;
    },
  },
});

// html function call
<div v-on:click="writeText">{{ text }}</div>;
```

### class binding

> syntax:

```html
<div v-bind:class="{ [class name]: [Vue data] }"></div>
```

```html
<style>
  .active {
    color: blue;
  }
</style>

<div id="app">
  <div v-bind:class="{ active = isActive }">
    if the value of isActive true then active calss will be added to this div
  </div>
</div>

<script>
  var app = new Vue({
    el: "#app",
    data: {
      isActive: true,
    },
  });
</script>
```

### style binding

> syntax:

```html
<div v-bind:style="{ [style name]: [Vue data] }"></div>
```

```html
<div id="app">
  <div v-bind:style="{ color: activeColor, fontSize: fontSize + 'px' }">
    if the value of isActive true then active calss will be added to this div
  </div>
</div>

<script>
  var app = new Vue({
    el: "#app",
    data: {
      activeColor: "red",
      fontSize: 30,
    },
  });
</script>
```

### computed

> syntax:

```js
var app = new Vue({
  el: "#app",
  data: {
    message: "Hello Vue!",
  },
  computed: {
    [Vue computed method]: function () {
      // code
    },
  },
});
```

```jsx
const app = Vue.createApp({
  data() {
    return {
      text: "",
      movileNav: false,
    };
  },
  computed: {
    textLength() {
      return this.text.length;
    },
    openNav() {
      // return this.mobileNav ? "open" : "";
      if (this.mobileNav) {
        return "open";
      } else {
        return "";
      }
    },
  },
});

// html function call
<div>{{ textLength }}</div>;
```

## Components

## es6-string-html for color component show in template

```js

// this is a separate component
app.component("color", {
  props: ["color"],
  template: /*html*/ `<div class="color" :style="{backgroundColor: color}"></div>`,
});

// now to use them in html
// import the file first like <script src="fileName.js"></script>
// then use it like this
<color :color="red"></color>
```

## vue $emit

> i have a single page website. now in this website there has a button . when we click the button then a modal will be open. now i want to close the modal when i click outside of the modal. so i have to use $emit. now i will show you how to use $emit.

```js
// this is the modal component
app.component("modal", {
  template: /*html*/ `
    <div class="modal" @click="hideOrderForm">
      <div class="modal-content">
        <slot></slot>
      </div>
    </div>
  `,
  data() {
    return {};
  },
  methods: {
    hideOrderForm() {
      this.$emit("toggle-order-form"); // this is the $emit
    },
  },
});
```

```jsx
//now main vue file or index file.
<order-form
              :cart="cart"
              :total="total"
              v-if="showModal"
              @toggle-order-form="toggleModal" // here the $emit is used
            >
</order-form>
```

```js
const app = Vue.createApp({
  data() {
    return {
      showModal: false,
    };
  },
  methods: {
    toggleModal() {
      this.showModal = !this.showModal;
    },
  },
});
```
