<script setup>
import IconHome from '@/components/icons/IconHome.vue'
import IconAbout from '@/components/icons/IconAbout.vue'
import IconDiscord from '@/components/icons/IconDiscord.vue'
import IconLodestone from '@/components/icons/IconLodestone.vue'
</script>

<template>
    <nav>
        <RouterLink to="/"><IconHome /></RouterLink>
        <RouterLink to="/about"><IconAbout /></RouterLink>
        <RouterLink to="/discord"><IconDiscord /></RouterLink>
        <a href="https://fr.finalfantasyxiv.com/lodestone/freecompany/9233364398528010620/" target="_blank"><IconLodestone /></a>
    </nav>
</template>

<style scoped>
    nav{
        min-width: 250px;
        display: flex;
        justify-content: space-between;
        text-transform: uppercase;
        font-size: 2rem;
    }
    a{
        width: 4rem;
        height: 4rem;
        padding: 1rem;
        display: flex;
        justify-content: center;
        align-items: center;
        color: var(--light);
        /* border: .1rem solid currentColor; */
        opacity: .5;
        transition: opacity .3s ease;
    }

    @media (hover: hover){
        a:hover{
            opacity: 1;
            transition: opacity .3s ease;
        }
    }
    @media screen and (orientation: portrait){
        nav{
            width: 100%;
            pointer-events: all;
        }
        a{
            width: calc(100% / 4);
            height: 5rem;
            /* padding: 1rem; */
        }
    }
</style>