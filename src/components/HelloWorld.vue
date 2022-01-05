<template>
  <div>
    <button @click="addSize()">点我+</button>
    <button @click="reduceSize()">点我--------</button>
    <p :style="{fontSize: size + 'px'}">这是段落标签</p>

    <ol>
      <li>姓名：{{name}}</li>
      <li>年龄：{{age}}</li>
      <li>年龄2：{{age2}}</li>
      <li>年龄2：{{age3}}</li>
    </ol>
  </div>
</template>

<script>
import { ref, isRef, unref, reactive, toRefs, toRef } from '@vue/composition-api';
export default {
  setup(){
    const size = ref(50);
    const addSize = ()=>{
      if(isRef(size)) size.value++;
      info.age++
    }
    const reduceSize = ()=>{
      if(isRef(size)) size.value--;
      age2.value--;
    }

    const qwe = 10;
    console.log(unref(qwe));

    const info = reactive({
      name:'张三',
      age:18
    })

    const age2 = toRef(info,'age');
    const age3 = ref(info.age);


    return {
      size,
      ...toRefs(info),
      age2,
      age3,
      addSize,
      reduceSize
    }
  }
}
</script>

<style>

</style>