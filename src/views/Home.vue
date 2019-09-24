<template>
  <div class="home">
        <div>
            我叫{{name}}
        </div>
        <!-- v-for里面的itme代表数据的每一项，index代表这一项的下标 -->
        <div v-for='(item,index) in arr' :key="index">
            <div @click="clickName(item,index)" class="item" :class="{back:index === num,color:index === num}" :style="{color:color}">
              {{item.name}} --- {{item.price}}
            </div>
        </div>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'home',
        data() {
            return {
                num:0,
                name: 'suibian',
                color:'red',
                arr: [{
                  name: 'yu',
                  price: 21
                },
                {
                  name: 'jck',
                  price: 28
                }, 
                {
                  name: 'j',
                  price: 19
                  }]
                }
            },
            methods: {
                clickName(item,index){
                    //alert(item.name+" "+item.price+" "+index)
                    this.num=index
                }
            },
}
</script>

<style  scoped>
.home{

}
.itme{
  border: 1px solid red;
  margin: 10px 0;
}
.back{
  background: skyblue;
}
.color{
  color: greenyellow !important;
}
</style>