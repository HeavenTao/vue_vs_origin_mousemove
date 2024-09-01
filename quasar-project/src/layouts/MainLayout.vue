<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn flat dense round icon="menu" aria-label="Menu" @click="leftDrawerOpen = !leftDrawerOpen" />

        <q-toolbar-title>
          Quasar App
        </q-toolbar-title>

        <div>Quasar v{{ $q.version }}</div>
      </q-toolbar>
    </q-header>

    <q-page-container>
      <q-page class="row">
        <div class="col-6" style="border-right: solid 1px lightgray;">
          <div>Vue对象绑定</div>

          <use-vue></use-vue>
        </div>
        <div class="col-6">
          <div>Js原生</div>

          <use-js></use-js>
        </div>
      </q-page>
    </q-page-container>
  </q-layout>
</template>

<script>
import UseVue from "../components/UseVue.vue"
import UseJs from "../components/UseJs.vue"

export default {
  name: 'MainLayout',
  components: { UseVue, UseJs },
  data() {
    return {
      leftDrawerOpen: false,
    }
  }
}
</script>
