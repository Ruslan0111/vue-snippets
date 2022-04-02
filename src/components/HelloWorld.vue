<script setup>
/* eslint-disable */
import { TabGroup, TabList, Tab, TabPanels, TabPanel } from "@headlessui/vue";
defineProps({
  msg: {
    type: String,
    required: true,
  },
});
</script>

<template>
  <div class="greetings">
    <TabGroup>
      <TabList>
        <Tab v-slot="{ selected }"
          ><span :class="{ selected: selected }">Tab 1</span></Tab
        >
        <Tab v-slot="{ selected }"
          ><span :class="{ selected: selected }">Tab 2</span></Tab
        >
        <Tab v-slot="{ selected }"
          ><span :class="{ selected: selected }">Tab 3</span></Tab
        >
      </TabList>
      <TabPanels>
        <TabPanel v-slot="{ selected }"
          ><span :class="{ selected: selected }">Content 1</span></TabPanel
        >
        <TabPanel v-slot="{ selected }"
          ><span :class="{ selected: selected }">Content 2</span></TabPanel
        >
        <TabPanel v-slot="{ selected }"
          ><span :class="{ selected: selected }">Content 3</span></TabPanel
        >
      </TabPanels>
    </TabGroup>
    <h1 class="green">{{ msg }}</h1>
    <h3>
      You’ve successfully created a project with
      <a target="_blank" href="https://vitejs.dev/">Vite</a> +
      <a target="_blank" href="https://vuejs.org/">Vue 3</a>.
    </h3>
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

.selected {
  color: red;
  animation: fade 2s ease 0s 1;
}

@keyframes fade {
  from {
    opacity: 0;
  }

  to {
    opacity: 1;
  }
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
