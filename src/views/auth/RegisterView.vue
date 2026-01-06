<template>
    <HeaderMain />
    <div class="register-view">
        <RegisterBanner class="banner-section" />
        <RegisterForm class="form-section" />
    </div>
</template>

<script setup>
import { RegisterBanner, RegisterForm, HeaderMain } from '@/components';
</script>

<style scoped>
.register-view {
    display: grid;
    grid-template-columns: 1.3fr 1fr;
    min-height: 100vh;
}

.banner-section {
    position: sticky;
    top: 0;
    height: 100vh;
}

.form-section {
    overflow-y: auto;
}

@media (max-width: 1024px) {
    .register-view {
        grid-template-columns: 1fr;
    }

    .banner-section {
        position: relative;
        height: auto;
        min-height: 60vh;
    }
}
</style>