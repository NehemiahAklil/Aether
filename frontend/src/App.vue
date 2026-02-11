<script lang="ts" setup>
import { Button } from './components/ui/button';
import { Icon } from '@iconify/vue';
import AppSidebar from '@/components/AppSidebar.vue'
import { SidebarProvider, SidebarTrigger } from '@/components/ui/sidebar'
</script>

<template>
    <SidebarProvider>
        <AppSidebar />
        <main>
            <SidebarTrigger />
            <slot />
        </main>
    </SidebarProvider>
</template>
