<script setup lang="ts">
import { onMounted } from 'vue'
import { storeToRefs } from 'pinia'
import { RouterLink, RouterView } from 'vue-router'
import { useDeliveryStore } from './store'
const store = useDeliveryStore()
const { approvedShare, offers, urgent } = storeToRefs(store)
onMounted(store.load)
</script>

<template><div class="shell"><aside><div class="brand">Mediterranean30<span>ACTION DELIVERY</span></div><nav><RouterLink to="/">Action initiatives</RouterLink><RouterLink to="/insights">Delivery guidance</RouterLink></nav><div class="health"><i /> Java action service connected</div></aside><main><header><div><span class="eyebrow">Deliver a connected, prosperous, resilient and secure Common Mediterranean Space</span><h1>Mediterranean Action Plan Delivery Desk</h1></div><button @click="store.addOffer">Add action initiative</button></header><section class="summary"><article><small>Initiatives approved</small><strong>{{ approvedShare }}%</strong><div class="bar"><span :style="{ width: `${approvedShare}%` }" /></div></article><article><small>Initiatives tracked</small><strong>{{ offers.length }}</strong><p>Shared action view</p></article><article><small>Urgent delivery gaps</small><strong>{{ urgent }}</strong><p>Needs attention</p></article></section><RouterView /></main></div></template>
