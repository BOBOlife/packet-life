<template>
  <div>
    <ul class="types">
      <li :class="type === '-'&& 'selected'" @click="selectType('-')">支出</li>
      <li :class="type === '+'&& 'selected'" @click="selectType('+')">收入</li>
    </ul>
  </div>
</template>

<script lang="ts">
  import Vue from 'vue';
  import {Component} from 'vue-property-decorator';

  // @Component //装饰器 ，将选项装饰成成构造选项的模样
  @Component({
    props: {
      propMessage: String
    }
  })
  export default class Types extends Vue {
    type = '-'; // '-'表示支出，‘+’表示收入
    helloMsg = 'hello, ' + this.propMessage;

    selectType(type: string) {    //type只能是‘-’或‘+’中的一个
      if (type !== '-' && type !== '+') {
        throw new Error('Type is unknown !');
      }
      this.type = type;
    }
  }

  // export default {
  //   name: 'Types',
  //   data() {
  //     return {
  //       type: '-' // '-'表示支出，‘+’表示收入
  //     };
  //   },
  //   methods: {
  //     selectType(type) { // type 只能是‘-’或‘+’中的一个
  //       if (type !== '-' && type !== '+') {
  //         throw new Error('Type is unknown !');
  //       }
  //       this.type = type;
  //     }
  //   }
  // };
</script>

<style lang="scss" scoped>
  .types {
    background: #c4c4c4;
    display: flex;
    text-align: center;
    font-size: 24px;

    > li {
      width: 50%;
      line-height: 64px;
      display: flex;
      justify-content: center;
      align-items: center;
      position: relative;

      &.selected::after {
        content: '';
        position: absolute;
        bottom: 0;
        left: 0;
        width: 100%;
        height: 4px;
        background: #333;
      }
    }
  }

</style>