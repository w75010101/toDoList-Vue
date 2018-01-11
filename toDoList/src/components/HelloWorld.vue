<template>
  <div class="hello">
    <input type="text" v-model="iptStr"><button @click="add">+</button><button @click="deleteAll">删除全部</button>
    <ul>
      <li v-for="(item , index) in iptArr" :key="index">{{index + 1}}.{{item}}
        <button @click="del(index)">-</button>
        <button @click="update(item, index)">修改</button>
      </li>
    </ul>
    <div class="cover" v-if="coverShowBl">
      <div class="box">
        <input type="text" v-model="updateStr">
        <button @click="save">保存</button>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      iptStr: '',
      iptArr: [],
      iptShowBl: false,
      coverShowBl: false,
      updateStr: '',
      nowValue: '',
      nowIndex: ''
    }
  },
  methods: {
    add () {
      this.iptArr.push(this.iptStr);
      this.iptStr = ''
    },
    del (index) {
      this.iptArr.splice(index, 1)
    },
    deleteAll () {
      this.iptArr = []
    },
    update (index) {
      this.coverShowBl = true;
      this.nowIndex = index
      console.log(this.nowIndex, this.nowValue)
    },
    save (){
      this.iptArr.splice(this.nowIndex, 1, this.updateStr);
      this.iptShowBl = false;
      this.coverShowBl = false;
    }
  }
}
</script>

<style scoped>
  .cover {
    position: absolute;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,.5);
  }
  .cover .box {width: 300px; height: 150px; background: #fff; position: absolute; left: 50%; top: 50%; margin-left: -150px; margin-top: -70px; display: flex; justify-content: space-around; align-items: center; flex-direction: column}
</style>
