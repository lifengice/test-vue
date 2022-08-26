<!--
 * @Author: lifengice lifengice@126.com
 * @Date: 2022-08-26 14:24:19
 * @LastEditors: lifengice lifengice@126.com
 * @LastEditTime: 2022-08-26 15:43:51
 * @FilePath: /test-vue/src/components/HelloWorld.vue
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->
<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>
      For a guide and recipes on how to configure / customize this project,
      <br>check out the
      <a
        href="https://cli.vuejs.org"
        target="_blank"
        rel="noopener"
      >vue-cli documentation</a>.
    </p>
    <h3>Installed CLI Plugins</h3>
    <input v-model="fruitName" placeholder="添加一种水果吧">
    <input v-model="fruitEName" placeholder="英文名叫啥">
    <button @click="addFruit">确定</button>
    <ul>
      <li v-for="(item ,index) in items" :key="item.id" @click="removeme(index)">{{item.name}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",

  props: {
    msg: String
  },

  data() {
    return {
      maxid: 3,
      fruitName: "",
      fruitEName: "",
      items: [
        { id: 1, name: "大蒜", ename: "banana" },
        { id: 2, name: "苹果", ename: "apple" }
      ]
    };
  },

  methods: {
    removeme(index) {
      console.log(index);
      this.items.splice(index,1);
      // console.log(index);
    },
    addFruit() {
      if (!this.fruitName || !this.fruitEName) return;
      this.items.push({
        id: this.maxid++,
        name: this.fruitName,
        ename: this.fruitEName
      });
      console.log(this.items);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  /* display: inline-block; */
  margin: 0 10px;
}
a {
  color: red;
}
</style>
