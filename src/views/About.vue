<template>
  <div class="container">
    <div class="box1">
      <div v-if="arr1.length > 0">
        <div v-for="(item, index) in arr1" :key="item.id">
          <div @click="clickItem1(item, index)" :class="{'active': activeIndex === index}">{{item.name}}</div>
        </div>
      </div>
      <div v-else>暂无数据</div>
    </div>
    <div class="center">
      <div @click="right">&gt;</div>
      <div @click="left">&lt;</div>
    </div>
    <div class="box2">
      <div v-if="arr2.length > 0">
        <div v-for="(item, index) in arr2" :key="item.id">
          <div @click="clickItem2(item, index)" :class="{'active': activeIndex === index + arr1.length}">{{item.name}}</div>
        </div>
      </div>
      <div v-else>暂无数据</div>
    </div>
  </div>

</template>

<script>
  export default {
    name: "demo",
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
            name: 'jack',
          },
          {
            id: 3,
            name: 'rose',
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
        ],
        activeIndex: -1,
        activeItem: {}
      }
    },
    methods: {
      clickItem1 (item, index) {
        this.activeIndex = index
        this.activeItem = item
      },
      clickItem2 (item, index) {
        this.activeIndex = index + this.arr1.length
        this.activeItem = item
      },
      right () {
        if (this.activeIndex < this.arr1.length && this.activeIndex >= 0) {
          this.arr1.splice(this.activeIndex, 1)
          this.arr2.push(this.activeItem)
          this.activeIndex = -1
        }
      },
      left () {
        if (this.activeIndex >= this.arr1.length && this.activeIndex >= 0) {
          this.arr2.splice((this.activeIndex - this.arr1.length), 1)
          this.arr1.push(this.activeItem)
          this.activeIndex = -1
        }
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
  .box1 div,.box2 div {
    margin: 5px 0;
    cursor: pointer;
  }
  .active {
    background: skyblue;
  }
  .center {
    height: 400px;
    padding-top: 180px;
  }
  .center div {
    cursor: pointer;
    margin: 10px 0;
  }
</style>
