<template>
  <div class="accordion-item" :class="{'active': active}">
    <div class="item-head" @click="click">
      {{ title }}
      <i class="item-arrow mintui mintui-back"></i>
    </div>
    <el-collapse-transition>
      <div class="item-body" ref="body" v-show="active">
        <slot></slot>
      </div>
    </el-collapse-transition>
  </div>
</template>

<style scoped lang="scss">
  .item-head {
    height: 43px;
    line-height: 43px;
    padding-left: 15px;
    background-color: #fff;
    color: #48576a;
    cursor: pointer;
    border-bottom: 1px solid #dfe6ec;
    font-size: 13px;
  }

  .item-body {
    will-change: height;
    background-color: #fff;
    overflow: hidden;
    border-bottom: 1px solid #dfe6ec;
    overflow: auto;
    color: #333;
    font-size: 13px;
    color: #1f2d3d;
    line-height: 1.769230769230769;
    padding: 10px 15px;
    transition: height .5s;
  }

  .item-arrow {
    margin-right: 8px;
    transition: transform .3s;
    float: right;
    transform: rotate(180deg);
  }

  .accordion-item {
    &.active {
      .item-arrow {
        transform: rotate(270deg);
      }
    }
  }
</style>

<script>
  import CollapseTransition from 'element-ui/lib/transitions/collapse-transition'

  export default {
    name: 'accordion-item',
    components: {
      'el-collapse-transition': CollapseTransition
    },
    props: {
      name: '',
      title: ''
    },
    data () {
      return {
        active: false
      }
    },
    mounted () {
      this.$parent.add(this)
    },
    methods: {
      click () {
        this.$parent.doClick(this.name)
        this.active = !this.active
      }
    }
  }
</script>