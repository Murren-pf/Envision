<template>

  <v-navigation-drawer
    fixed
    clipped
    class="grey lighten-4"
    app
    v-model="drawer"
    style="z-index: 1"
    :mini-variant="mini"
  >

    <v-toolbar flat class="transparent">
      <v-list class="pa-0" dense>
        <v-list-tile>
          <v-list-tile-action>
            <v-btn icon @click="mini = !mini">
              <v-icon v-if="!mini">chevron_left</v-icon>
              <v-icon v-if="mini">chevron_right</v-icon>
            </v-btn>
          </v-list-tile-action>
          <v-list-tile-content style="font-size:12px; color: grey">收回菜单</v-list-tile-content>
        </v-list-tile>
        <v-divider></v-divider>
      </v-list>
    </v-toolbar>

    <v-list dense class="grey lighten-4">
      <template v-for="(item, i) in items">
        <v-layout row v-if="item.heading" align-center :key="i">
          <v-flex xs6>
            <v-subheader v-if="item.heading">
              {{ item.heading }}
            </v-subheader>
          </v-flex>
        </v-layout>
        <v-divider dark v-else-if="item.divider" class="my-3" :key="i"></v-divider>
        <v-list-tile :key="i" v-else :to="item.link">
          <v-list-tile-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title>
              <span class="grey--text text--darken-1">{{ item.text }}</span>
            </v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
      </template>
    </v-list>
  </v-navigation-drawer>
</template>

<script>
import axios from 'axios'
export default {
  data: () => ({
    drawer: null,
    mini: false,
    items: [
      { heading: '视图' },
      { icon: 'home', text: '首页' },
      { icon: 'school', text: '学习',link: '/todolist/new' },
      { icon: 'forum', text: '论坛' },
      { icon: 'public', text: '探索' },
      { icon: 'person', text: '个人中心' },
      { icon: 'create', text: '创作' },
      { icon: 'group', text: '群组' },
      { icon: 'shopping_cart', text: '礼品店' },
      { icon: 'assignment', text: '社团事务',link: '/allequipment/new' },
      { icon: 'build', text: '管理后台' },
      { divider: true },
      { heading: '自定义链接' },
      { icon: 'add', text: '添加新的快速链接' },
    ]
  })
}
</script>

<style scoped>

</style>
