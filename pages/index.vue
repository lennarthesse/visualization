<template>
    <div class="content-wrapper">
        <h2 class="content-title">Visualisiserung</h2>
        <div class="visualization-tabs">
            <button
                class="tab-button unselect-button"
                :class="{ active: !activeTab }"
                @click="unselectTab()"
            >
                #x2716; No selection
            </button>
            <!-- Existing visualization tabs-->
            <button
                v-for="tab in visualizations"
                :key="tab.id"
                :class="['tab-button', { active: activeTab === tab.id }]"
                @click="setActiveTab(tab.id)"
            >
                {{ tab.name }}
            </button>
        </div>

        <div class="visualization-container">
            <!-- Loading state -->
            <div v-if="loading" class="loading-state">
                <p>Lade Visualisierung...</p>
            </div>
            <!-- Shuffle -->
            <div v-else-if="activeTab === 'shuffle'" class="visualization">
                <ShuffleSelector />
            </div>
            <!-- Charts visualization -->
            <div v-else-if="activeTab === 'chart'" class="visualization">
                <ChartSelector />
            </div>
            <!-- Scatter plot visualization -->
            <div v-else-if="activeTab === 'dot-plot'" class="visualization">
                <ScatterSelector />
            </div>
            <!-- Default state when nothing is selected -->
            <div v-else class="visualization empty-state">
                <div class="placeholder">
                    <h3>Keine Visualisierung ausgewählt</h3>
                    <p>Bitte wählen Sie eine Visualisierung aus den Tabs oben.</p>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">
    import type { active } from 'd3';
    import { ref, onMounted } from 'vue';
    import ShuffleSelector from '~/components/ShuffleSelector.vue';
    //import ChartSelector from '~/components/ChartSelector.vue';
    //import ScatterSelector from '~/components/ScatterSelector.vue';

    // Define layout - redundant for default layout
    definePageMeta({
    layout: 'default'
    });

    // Available visualizations
    const visualizations = [
        { id: 'shuffle', name: 'Shuffle' },
        { id: 'chart', name: 'Chart' },
        { id: 'dot-plot', name: 'Dot Plot' },
    ];

    // UI state - no tab selected by default
    const activeTab = ref('');
    const loading = ref(false);

    // Simulate loading when changing tabs
    function setActiveTab(tabId: string) {
        loading.value = true;
        activeTab.value = tabId;
        
        // Simulate loading delay
        setTimeout(() => {
            loading.value = false;
        }, 300);
    }

    // Unselect the current tab
    function unselectTab() {
        loading.value = true;
        activeTab.value = '';
        setTimeout(() => {
            loading.value = false;
        }, 300);
    }

    onMounted(() => {
    // Initially no loading needed
    loading.value = false;
    });
</script>

<style scoped>
    .content-wrapper {
        max-width: 1200px;
        margin: 0 auto;
        padding: 1rem;
    }
</style>