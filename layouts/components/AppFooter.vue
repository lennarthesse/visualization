<template>
    <footer class="app-footer">
        <div class="footer-content">
            <p class="copyright">&copy; {{ currentYear }} Studiengang Medieninformatik.</p>
            <div class="footer-links">
                <a href="https://www.medieninformatik.de" target="_blank">Blog des Studiengangs</a>
            </div>
        </div>
    </footer>
</template>

<script setup lang="ts">
    import { ref, onMounted } from 'vue';
    // Reactive current year for copyright
    const currentYear = ref(new Date().getFullYear());
</script>

<style scoped>
    .app-footer {
        background-color: #f8f9fa;
        border-top: 1px solid #e9ecef;
        padding: 1.5rem 0;
        margin-top: 2rem;
        width: 100%;
    }

    .footer-content {
        max-width: 1200px;
        margin: 0 auto;
        padding: 0 1rem;
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 1rem;
    }

    .copyright {
        margin: 0;
        color: #6c757d;
        font-size: 0.9rem;
    }

    .footer-links {
        display: flex;
        gap: 1.5rem;
    }

    .footer-links a {
        color: #6c757d;
        text-decoration: none;
        font-size: 0.9rem;
        transition: color 0.2s ease;
    }

    .footer-links a:hover {
        color: #495057;
    }

    @media screen and (min-width: 768px) {
        .footer-content {
            flex-direction: row;
            justify-content: space-between;
        }
    }
</style>