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
    <Sidebar>
        <SidebarContent>
            <SidebarGroup>
                <SidebarGroupLabel>Application</SidebarGroupLabel>
                <SidebarGroupContent>
                    <SidebarMenu>
                        <SidebarMenuItem v-for="item in items" :key="item.title">
                            <SidebarMenuButton as-child>
                                <a :href="item.url">
                                    <Icon :icon="item.icon" class="text-3xl text-indigo-600" />
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
