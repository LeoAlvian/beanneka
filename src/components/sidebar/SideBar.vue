<template>
    <div class="sidebar" :style="{ width: sidebarWidth }">
        <h1 class="title-app">
            <span v-if="collapsed" class="app-name">
                <div>B</div>
                <div>C</div>
            </span>
            <span v-else class="app-name">
                Beanneka Coffee
            </span>
        </h1>

        <SidebarLink to="/" icon="fas fa-home">Home</SidebarLink>
        <SidebarLink to="/dashboard" icon="fas fa-columns">Dashboard</SidebarLink>
        <SidebarLink to="/analytics" icon="fas fa-chart-bar">Analytics</SidebarLink>
        <SidebarLink to="/about" icon="fas fa-users">About</SidebarLink>
        <!-- <SidebarLink to="/image" icon="fas fa-image">Images</SidebarLink> -->

        <span 
        class="collapse-icon"
        :class="{ 'rotate-180' : collapsed }"
        @click="toggleSidebar">
            <font-awesome-icon :icon="['fas', 'angles-left']" /> 
        </span>

    </div>    
</template>

<script>

import { collapsed, toggleSidebar, sidebarWidth } from './State'
import SidebarLink from './SidebarLink.vue'

export default {
    props: {},
    components: { SidebarLink },
    setup() {
        return { collapsed, toggleSidebar, sidebarWidth }
    }
}
</script>

<style scoped>
.title-app {
    margin: 1rem;
}

 .sidebar {
    color: var(--blue2);
    background-color: var(--latte);

    float: left;
    position: fixed;
    z-index: 1;
    top: 0;
    left: 0;
    bottom: 0;
    padding: .5rem 0 .5rem .5rem;

    transition: 0.3s ease;

    display: flex;
    flex-direction: column;
 }


 .collapse-icon {
    position: absolute;
    bottom: 0;
    padding: 0.75rem;
    cursor: pointer;

    color: var(--blue2);

    transition: 0.2s linear;
 }

 .collapse-icon:hover {
    transform: scale(120%);
 }

 .rotate-180 {
    transform: rotate(180deg);
    transition: 0.2s linear;
 }
</style>