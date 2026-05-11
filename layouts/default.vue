<template>
    <div class="app-layout">
        <AppHeader />
        <main class="main-content">
            <slot />
        </main>
        <AppFooter />
    </div>
</template>

<script setup>
    import AppHeader from '@/layouts/components/AppHeader.vue';
    import AppFooter from '@/layouts/components/AppFooter.vue';
</script>

<style scoped>
    .app-layout {
        min-height: 100vh;
        display: flex;
        flex-direction: column;
    }

    .main-content {
        flex: 1;
        padding: 1rem;
        max-width: 1200px;
        width: 100%;
        margin: 0 auto;
    }
</style>