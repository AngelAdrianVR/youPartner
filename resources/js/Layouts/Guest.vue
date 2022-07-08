<script setup>
import BreezeApplicationLogo from '@/Components/ApplicationLogo.vue';
import { Link } from '@inertiajs/inertia-vue3';
</script>

<template>
    <div class="min-h-screen flex flex-col sm:justify-center items-center pt-6 sm:pt-0 bg-gradient-to-r from-sky-400 to-indigo-400">
        <div>
            <Link href="/">
                <BreezeApplicationLogo class="w-20 h-20 fill-current bg-transparent mt-2" />
            </Link>
        </div>

        <div class="w-full sm:max-w-md mt-6 px-6 py-4 bg-gray-300 shadow-md overflow-hidden sm:rounded-lg">
            <slot />
        </div>
    </div>
</template>
