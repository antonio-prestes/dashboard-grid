<template>
  <q-layout view="hHh lpR fFf">

    <q-header elevated class="bg-primary text-white">
      <q-toolbar>
        <q-btn dense flat round icon="menu" @click="toggleLeftDrawer" />

        <q-toolbar-title>
          <q-avatar>
            <img src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg">
          </q-avatar>
          Title
        </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="drawer"
      show-if-above
      :mini="miniState"
      @mouseover="miniState = false"
      @mouseout="miniState = true"
      :width="200"
      :breakpoint="500"
      bordered
      :class="$q.dark.isActive ? 'bg-grey-9' : 'bg-grey-3'"
    >
      <q-scroll-area class="fit" :horizontal-thumb-style="{ opacity: 0 }">
        <q-list padding>
          <q-item clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="inbox" />
            </q-item-section>
            <q-item-section>
              Inbox
            </q-item-section>
          </q-item>

          <q-item active clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="star" />
            </q-item-section>
            <q-item-section>
              Star
            </q-item-section>
          </q-item>

          <q-item clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="send" />
            </q-item-section>
            <q-item-section>
              Send
            </q-item-section>
          </q-item>

          <q-separator />

          <q-item clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="drafts" />
            </q-item-section>
            <q-item-section>
              Drafts
            </q-item-section>
          </q-item>
        </q-list>
      </q-scroll-area>
    </q-drawer>

    <q-page-container>
      <div class="grid-stack">
        <div
          v-for="(component, index) in components"
          :key="index"
          class="grid-stack-item"
          gs-w="6"
          gs-h="1"
        >
          <div class="grid-stack-item-content">
            <component :is="component" />
          </div>
        </div>
      </div>
    </q-page-container>

  </q-layout>
</template>

<script>
import { onMounted, ref } from 'vue'
import 'gridstack/dist/gridstack.min.css';
import { GridStack } from 'gridstack';
import ComponentA from '@/components/ComponentA.vue'
import ComponentB from '@/components/ComponentB.vue'
import ComponentC from '@/components/ComponentC.vue'
import ComponentD from '@/components/ComponentD.vue'

export default {
  components: { ComponentA, ComponentB, ComponentC, ComponentD },
  setup() {
    const components = ref(['ComponentA', 'ComponentB', 'ComponentC', 'ComponentD']);
    const leftDrawerOpen = ref(false);
    const drawer = ref(false);
    const miniState = ref(true);

    onMounted(() => {
      GridStack.init({
        float: true,
        cellHeight: 350,
        minRow: 2,
        maxRow: 2,
        disableResize: true,
        disableOneColumnMode: true
      });
    });

    const toggleLeftDrawer = () => {
      leftDrawerOpen.value = !leftDrawerOpen.value;
    };

    return {
      components,
      drawer,
      miniState,
      leftDrawerOpen,
      toggleLeftDrawer
    }
  }
}
</script>

<style type="text/css">
.grid-stack-item-content { border: 2px solid red; }
</style>