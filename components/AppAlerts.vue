<script setup lang="ts">
const { alerts, success, error, warning, info, dismiss } = useAlerts();
</script>
<template>
  <div
    class="fixed bottom-0 z-10 w-full p-2 right-2 sm:p-0 sm:w-auto sm:bottom-5"
  >
    <TransitionGroup name="list" tag="ul">
      <div
        v-for="alert in alerts"
        :key="alert.id"
        class="mb-4 border-t-[1px] shadow-sm alert !pr-0"
        :class="`border-t-${alert.type} alert-${alert.type}`"
      >
        <div class="flex justify-between sm:w-80">
          <div class="flex items-center">
            <AlertIcon :type="alert.type" />
            <div class="mx-4">
              <div class="font-bold" v-if="alert.title">{{ alert.title }}</div>
              <div class="">{{ alert.message }}</div>
            </div>
          </div>
          <button
            v-if="alert.dismissiable"
            @click="dismiss(alert)"
            class="p-1 transition rounded btn-ghost"
          >
            x
          </button>
        </div>
      </div>
    </TransitionGroup>
  </div>
</template>
