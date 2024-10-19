<template>
  <router-link :to="to" class="link" :class="{ active: isActive }">
    <i class="icon" :class="icon" />
    <transition name="fade">
        <span v-if="!collapsed">
            <slot />
        </span>
    </transition>
  </router-link>
</template>

<script>
import { computed } from 'vue'
import { useRouter } from 'vue-router'
import { collapsed } from './State'


export default {
    props: {
        to: { type: String, required: true},
        icon: { type: String, required: true}
    },
    setup (props) {
        const route = useRouter()
        const isActive = computed(() => route.path === props.to)

        return { isActive, collapsed }
    }
}
</script>

<style scoped>
.link {
    display: flex;
    align-items: center;

    cursor: pointer;
    position: relative;
    font-weight: 400;
    user-select: none;

    margin: 0.1rem 0 0.1rem 0.5rem;
    padding: 0.4rem 0.4rem 0.4rem 0.6rem;
    border-top-left-radius: 50px;
    border-bottom-left-radius: 50px;
    height: 2.5rem;

    color: var(--blue2);
    text-decoration: none;
}

.link:hover {
    background-color: var(--blue2);
    color: var(--latte);
}


.router-link-active.router-link-exact-active.link{
    background-color: var(--blue2);
    color: var(--latte)
}

.router-link-active.router-link-exact-active.link:hover{
    color: var(--latte); 
}

.router-link-active.router-link-exact-active.link::before {
    content: '';
    position: absolute;
    top: -10px;
    right: 0;
    width: 10px;
    height: 10px;
    border-bottom-right-radius: 50px;
    box-shadow: 5px 5px 0 5px var(--blue2);
}

.router-link-active.router-link-exact-active.link::after {
    content: '';
    position: absolute;
    bottom: -10px;
    right: 0;
    width: 10px;
    height: 10px;
    border-top-right-radius: 50px;
    box-shadow: 5px -5px 0 5px var(--blue2);
}

.link .icon {
    flex-shrink: 0;
    width: 25px;
    margin-right: 10px;
}

.fade-enter-active,
.fade-leave-active {
    transition: opacity 0.1s ease-in-out;
}

.fade-enter-from,
.fade-leave-to {
    opacity: 0;
}
</style>