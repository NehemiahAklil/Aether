<script setup lang="ts">
import {
    Sidebar,
    SidebarContent,
    SidebarGroup,
    SidebarGroupContent,
    SidebarGroupLabel,
    SidebarMenu,
    SidebarMenuButton,
    SidebarMenuItem,
} from '@/components/ui/sidebar'
import { Icon } from '@iconify/vue';

// Menu items.
const items = [
    {
        title: 'Home',
        url: '#',
        icon: "solar:home-2-linear",
    },
    {
        title: 'Inbox',
        url: '#',
        icon: "solar:home-2-linear",
    },
    {
        title: 'Calendar',
        url: '#',
        icon: "solar:calendar-linear",
    },
    {
        title: 'Search',
        url: '#',
        icon: "solar:home-2-linear",
    },
    {
        title: 'Settings',
        url: '#',
        icon: "solar:settings-linear",
    },
]
</script>

<template>
    <Sidebar collapsible="icon">
        <SidebarHeader>
            <SidebarMenu>
                <SidebarMenuItem>
                    <SidebarMenuButton size="lg">
                        <div
                            class="flex aspect-square size-8 items-center justify-center rounded-lg bg-sidebar-primary text-sidebar-primary-foreground">
                            <GalleryVerticalEnd class="size-4" />
                        </div>
                        <div class="flex flex-col gap-0.5 leading-none">
                            <span class="font-semibold">Documentation</span>
                            <span class="">v1.0.0</span>
                        </div>
                    </SidebarMenuButton>
                </SidebarMenuItem>
            </SidebarMenu>
        </SidebarHeader>
        <SidebarContent>
            <SidebarGroup>
                <SidebarGroupLabel>Application</SidebarGroupLabel>
                <SidebarGroupContent>
                    <SidebarMenu>
                        <SidebarMenuItem v-for="item in items" :key="item.title">
                            <SidebarMenuButton as-child>
                                <a :href="item.url">
                                    <Icon :icon="item.icon" class="text-4xl text-amber-600" />
                                    <span>{{ item.title }}</span>
                                </a>
                            </SidebarMenuButton>
                        </SidebarMenuItem>
                    </SidebarMenu>
                </SidebarGroupContent>
            </SidebarGroup>
        </SidebarContent>
    </Sidebar>
</template>
