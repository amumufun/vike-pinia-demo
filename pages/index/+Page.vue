<template>
  <h1>My Vike + Vue app</h1>
  This page is:
  <ul>
    <li>Rendered to HTML.</li>
    <li>Interactive.</li>
  </ul>
  <h2>Counters synced via shared store</h2>
  <Counter />
  <hr />
  <Counter />
</template>

<script lang="ts" setup>
import { onServerPrefetch } from 'vue'
import { useData } from 'vike-vue/useData';
import type { Data } from './+data';
import Counter from '../../components/Counter.vue'
import { useCounterStore } from '../../stores/useCounterStore'

const preData = useData<Data>();

const { increment } = useCounterStore()
onServerPrefetch(() => {
  // Show that hydration works - the counter should start at 1
  increment()
})
</script>
