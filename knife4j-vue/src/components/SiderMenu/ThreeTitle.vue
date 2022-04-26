<template>
  <span>
    <my-icon v-if="item.icon" :type="item.icon"></my-icon>
<!--    <a-badge v-if="enableVersion&&item.hasNew" status="processing" title="新接口" style="margin-bottom:3px;"/>-->
    <span
      v-if="item.hasNew&&!collapsed"
      :class="item.menuClass"
      class="knife4j-menu-badge-num"
    >{{ num }}</span>
    <span>{{ item.name }}</span>
  </span>
</template>

<script>
  export default {
    props: {
      item: Object,
      collapsed: {
        type: Boolean,
        default: false
      }
    },
    data() {
      return {};
    },
    computed: {
      enableVersion() {
        return this.$store.state.globals.enableVersion;
      },
      num() {
        return this.item.children.filter(child => child.hasNew).length
      },
    }
  };
</script>

<style lang="stylus" scoped></style>
