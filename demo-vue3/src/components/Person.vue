<template>
  <div class="person">
    <h2>姓名：{{ person.name }}</h2>
    <h2>年龄：{{ person.age }}</h2>
    <button @click="changeName">修改姓名</button>
    <button @click="changeAge">修改年龄</button>
    <button @click="changePerson">修改整人</button>
  </div>
</template>

<script setup lang="ts" name="App">
  import {ref,computed, watch} from 'vue'

  let person = ref({
    name: '张三',
    age: 18
  })


  function changeName(){
    person.value.name += '~'
  }

  function changeAge(){
    person.value.age += 1
  }

  function changePerson(){
    person.value = {name: 'lisi', age: 90}
  }

  watch(person, (newValue, oldValue)=>{
    console.log('只把生变化', newValue, oldValue)
  },{deep:true, immediate:true})
</script>