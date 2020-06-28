<template>
  <div class="cell" @click="onClickSelf">
    <template v-if="status">
      <icon-svg class="cellicon" :icon-class="text" />
    </template>
    <template v-else></template>
  </div>
</template>

<script>
  import IconSvg from '@/components/IconSvg'
  export default {
    name: 'Cell',
    props: [ "n","res" ],
    data() {
      return {
        status: false,
        text: ""
      }
    },
    components: { IconSvg },
    methods: {
      onClickSelf() {
        console.log(this.res);
        if(this.text !== "" || this.res) {
          return;
        }
        this.status = true;
        this.text = this.n % 2 === 0 ? 'zu' : "yuan";
        this.$emit("click", this.text);
      }
    }
  };
</script>

<style scoped>
  .cell {
    border: 1px solid black;
    width: 100px;
    height: 100px;
    font-size: 50px;
    vertical-align: bottom;
    display: flex;
    justify-content: center;
    align-content: center;
    user-select: none;
  }
  .cellicon {
    margin: auto; /* 控制用户能否选中文本 */
  }
</style>