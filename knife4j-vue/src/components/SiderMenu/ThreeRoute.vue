<template>
  <router-link
    :class="{
            'knife4j-menu-api-deprecated':item.deprecated,
            [item.menuClass]:true
          }"
    :to="item.path"
  >
    <div class="menu-line">
      <div class="menu-item">
        <my-icon v-if="item.icon" :type="item.icon"></my-icon>
        <span v-if="item.method" class="knife4j-menu-line">{{ item.method }}</span>
        <span>{{ item.name }}</span>
      </div>
      <div class="menu-item menu-url" v-if="item.url">{{ item.url }}</div>
    </div>
    <a-badge v-if="enableVersion&&item.hasNew" status="processing" title="新接口" class="changed"/>
    </router-link>
</template>

<script>
  export default {
    props: {
      item: Object
    },
    data() {
      return {};
    },
    computed: {
      enableVersion() {
        return this.$store.state.globals.enableVersion;
      }
    }
  };
</script>

