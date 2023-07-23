```js
<script>
const value=4;

</script>
<template>
    <div>
    <div>Current Value: {{value}}</div>
    <div :style="{ color: value % 2 === 0 ? 'red' : 'green' }">
      {{value % 2 == 0 ? 'Value is even' : 'Value is odd'}}
    </div>
  </div>
</template>
```
