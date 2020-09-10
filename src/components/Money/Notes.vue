<template>
  <div>
    <label class="notes">
      <span class="name">{{this.fieldName}}</span>
      <input type="text" v-model="inputValue" :placeholder="placeholder">
    </label>
  </div>
</template>

<script lang="ts">
  import Vue from 'vue';
  import {Component, Watch, Prop} from 'vue-property-decorator';

  @Component
  export default class Notes extends Vue {
    @Prop() readonly value!: string;
    @Prop({required: true}) fieldName !: string;
    @Prop() placeholder?: string;
    inputValue = this.value;

    @Watch('inputValue')
    onValueChanged(val: string) {
      this.$emit('update:value', val);
    }
  }
</script>

<style lang="scss" scoped>
  .notes {
    font-size: 14px;
    background: #f5f5f5;
    padding-left: 16px;
    display: flex;
    align-items: center;

    .name {
      padding-right: 16px;
    }

    input {
      height: 64px;
      flex-grow: 1;
      background: transparent;
      border: none;
      padding-right: 16px;
    }
  }
</style>