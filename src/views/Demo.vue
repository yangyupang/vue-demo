<template>
  <div class="container">
    <div class="box1">
      <div v-if="arr1.length > 0" >
        <div v-for="(item, index) in arr1"  :key="item.id">
          <div @click="right(item, index)" class="box">{{item.name}}</div>
        </div>
      </div>
      <div v-else>暂无数据</div>
    </div>
    <div class="box2">
      <div v-if="arr2.length > 0">
        <div v-for="(item, index) in arr2" :key="item.id">
          <div @click="left(item, index)" class="box">{{item.name}}</div>
        </div>
      </div>
      <div v-else>暂无数据</div>
    </div>
  </div>

</template>

<script>
  export default {
    name: "demo1",
    components: {},
    props: {},
    data() {
      return {
        arr1: [
          {
            id: 1,
            name: 'tom'
          },
          {
            id: 2,
            name: 'jack'
          },
          {
            id: 3,
            name: 'rose'
          },
        ],
        arr2: [
          {
            id: 4,
            name: 'sky'
          },
          {
            id: 5,
            name: 'alex'
          },
          {
            id: 6,
            name: 'jay'
          },
        ]
      }
    },
    methods: {
      right (item, index) {
        this.arr1.splice(index, 1)
        this.arr2.push(item)
      },
      left (item, index) {
        this.arr2.splice(index, 1)
        this.arr1.push(item)
      }
    },
    mounted() {

    },
    created() {

    },
    filters: {},
    computed: {},
    watch: {},
    directives: {}
  }
</script>

<style scoped>
  .container {
    display: flex;
  }
  .box1,.box2 {
    width: 200px;
    height: 400px;
    border: 1px solid #eee;
    margin: 0 40px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
  .box1 div,.box2 div:first-child {
    margin: 15px 0;
    cursor: pointer;
  }
  .box {
    margin: 15px 0;
  }
</style>
