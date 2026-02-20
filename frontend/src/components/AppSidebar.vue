<script setup lang="ts">
import type { SidebarProps } from "@/components/ui/sidebar"
import { Icon } from "@iconify/vue"
import {
    Flame,
    Terminal,
    FolderOpen,
    Rocket,
    Cloud,
    Settings,
    Moon,
    Sun,
    PanelLeftClose,
    ArrowUpDown,
    LayoutGrid,
    Plus,
    Folder,
    FileText,
    Search
} from "lucide-vue-next"
import { h, ref, computed } from "vue"
import {
    Sidebar,
    SidebarContent,
    SidebarFooter,
    SidebarGroup,
    SidebarGroupContent,
    SidebarHeader,
    SidebarMenu,
    SidebarMenuButton,
    SidebarMenuItem,
    useSidebar,
} from "@/components/ui/sidebar"
import { Input } from "@/components/ui/input"
import { useColorMode } from '@vueuse/core'

const mode = useColorMode()

const toggleTheme = () => {
    mode.value = mode.value === 'dark' ? 'light' : 'dark'
}

const props = withDefaults(defineProps<SidebarProps>(), {
    collapsible: "icon",
})

const folders = [
    { title: "Config Files", url: "#" },
    { title: "Documentation", url: "#" },
    { title: "Scripts", url: "#" },
]

const recentNotes = [
    { title: "Vulkan Config", url: "#", active: true },
    { title: "Game Hunt Summary", url: "#" },
    { title: "Driving Routes", url: "#" },
    { title: "My Baby Seeds", url: "#" },
]

const tags = ["#linux", "#gpu", "#config"]

const activeNavIndex = ref<number>(0)

interface NavItem {
    icon: string,
    label: string
}
const navItems = ref<NavItem[]>([
    {
        icon: "solar:programming-outline",
        label: "Terminal"
    },
    {
        icon: "hugeicons:folder-03",
        label: "Folder"
    },
    {
        icon: "solar:rocket-2-outline",
        label: "Project"
    },
    {
        icon: "solar:cloud-outline",
        label: "Cloud"
    },

])

</script>

<template>
    <Sidebar class="overflow-hidden *:data-[sidebar=sidebar]:flex-row *:data-[sidebar=sidebar]:bg-transparent"
        v-bind="props">
        <!-- Primary Sidebar (Icons) -->
        <Sidebar collapsible="none" class="bg-workspace-bg w-12! border-r border-border-dark flex-shrink-0">
            <SidebarHeader class="py-4 flex items-center justify-center">
                <div class="text-primary hover:bg-white/5 p-1 rounded-lg transition-colors cursor-pointer mb-2">
                    <Flame :size="20" />
                </div>
                <div class="w-6 h-px bg-border-dark my-2"></div>
            </SidebarHeader>
            <SidebarContent class="flex flex-col items-center space-y-3 py-2 no-scrollbar">
                <SidebarMenu>
                    <SidebarMenuItem v-for="navItem, index in navItems" :key="index">
                        <SidebarMenuButton
                            class="w-10 h-10 p-0 flex items-center justify-center rounded-lg transition-all relative mx-auto"
                            :class="activeNavIndex === index ? 'bg-surface-dark text-primary shadow-[0_0_15px_rgba(255,191,0,0.15)] ring-1 ring-primary/30' : 'text-gray-500 hover:text-gray-300 hover:bg-white/5'"
                            @click="activeNavIndex = index">
                            <Icon :icon="navItem.icon" :width="20" />
                            <div v-if="activeNavIndex === index"
                                class="absolute left-[-10px] top-1/2 -translate-y-1/2 w-1 h-4 bg-primary rounded-r-full">
                            </div>
                        </SidebarMenuButton>
                    </SidebarMenuItem>
                </SidebarMenu>
            </SidebarContent>
            <SidebarFooter class="py-4 flex flex-col items-center space-y-3">
                <SidebarMenu>
                    <SidebarMenuItem>
                        <SidebarMenuButton
                            class="w-8 h-8 p-0 flex items-center justify-center rounded-lg text-gray-500 hover:text-primary hover:bg-white/5 transition-all"
                            @click="toggleTheme">
                            <Icon icon="solar:sun-outline" v-if="mode === 'dark'" :width="20" />
                            <Icon icon="solar:moon-landing-outline" v-else :width="20" />
                        </SidebarMenuButton>
                    </SidebarMenuItem>
                    <SidebarMenuItem>
                        <SidebarMenuButton
                            class="w-8 h-8 p-0 flex items-center justify-center rounded-lg text-gray-500 hover:text-primary hover:bg-white/5 transition-all">
                            <Settings :size="18" />
                        </SidebarMenuButton>
                    </SidebarMenuItem>
                    <SidebarMenuItem class="mt-2">
                        <div class="w-6 h-6 rounded-md overflow-hidden ring-1 ring-border-dark cursor-pointer">
                            <img alt="User"
                                src="https://lh3.googleusercontent.com/aida-public/AB6AXuDfVWz2KZlf9pB0z-6TiD_86w_yX94oeUsaefgGncL5gCqaxFoNYZ_XMoeHuQ-3G4ONGSlznW_WLuFr1ukj6hwivtmf8ZKb6tGtBn838eUyI-7I96a2ASkCdRZQ70zdNyclBXmYDFkOZYoiwMs1DZg1EQHbC1ZdzysZse2uQFOgEbWlb2ik6inaOq_xknF1I8mnlWYn7TWpHZeIkUmUBV9Wvrl97kmYglXZ5CWzDLohsGe1Cal-rCadbVJIDJ67pYlQbep_eYdTA2s"
                                class="w-full h-full object-cover" />
                        </div>
                    </SidebarMenuItem>
                </SidebarMenu>
            </SidebarFooter>
        </Sidebar>

        <!-- Secondary Sidebar (Content) -->
        <Sidebar collapsible="none"
            class="flex-1 bg-surface-light dark:bg-sidebar-bg border-r border-border-light dark:border-border-dark flex flex-col min-w-[256px]">
            <SidebarHeader
                class="h-14 border-b border-border-light dark:border-border-dark px-3 flex flex-row items-center justify-between gap-0">
                <div class="flex items-center">
                    <button class="p-1.5 rounded-md text-gray-400 hover:text-white hover:bg-white/5 transition-colors">
                        <PanelLeftClose :size="20" />
                    </button>
                </div>
                <div class="flex items-center space-x-1">
                    <button class="p-1.5 rounded-md text-gray-400 hover:text-white hover:bg-white/5 transition-colors"
                        title="Sort">
                        <ArrowUpDown :size="18" />
                    </button>
                    <button class="p-1.5 rounded-md text-gray-400 hover:text-white hover:bg-white/5 transition-colors"
                        title="View Options">
                        <LayoutGrid :size="18" />
                    </button>
                    <button class="p-1.5 rounded-md text-gray-400 hover:text-primary hover:bg-white/5 transition-colors"
                        title="New Note">
                        <Plus :size="18" />
                    </button>
                </div>
            </SidebarHeader>

            <SidebarContent class="flex-1 overflow-y-auto py-4 px-3 space-y-6">
                <!-- Workspace Title -->
                <div class="flex items-center px-2 pb-2">
                    <h2 class="text-sm font-semibold text-gray-800 dark:text-gray-200 tracking-wide font-serif">Arch
                        Linux</h2>
                    <span
                        class="ml-2 px-1.5 py-0.5 text-[10px] bg-primary/10 text-primary border border-primary/20 rounded">WS-1</span>
                </div>

                <!-- Folders -->
                <div>
                    <div class="flex items-center justify-between px-2 mb-2 group cursor-pointer">
                        <span
                            class="text-xs font-medium text-gray-500 uppercase tracking-wider group-hover:text-gray-300 transition-colors">Folders</span>
                        <Plus :size="14"
                            class="text-gray-600 group-hover:text-gray-400 opacity-0 group-hover:opacity-100 transition-all" />
                    </div>
                    <div class="space-y-0.5">
                        <a v-for="folder in folders" :key="folder.title"
                            class="flex items-center px-2 py-1.5 text-sm rounded-md text-gray-400 hover:text-gray-200 hover:bg-white/5 transition-colors"
                            href="#">
                            <Folder :size="18" class="mr-2 opacity-70" />
                            <span>{{ folder.title }}</span>
                        </a>
                    </div>
                </div>

                <!-- Recent Notes -->
                <div>
                    <div class="flex items-center justify-between px-2 mb-2 group cursor-pointer">
                        <span
                            class="text-xs font-medium text-gray-500 uppercase tracking-wider group-hover:text-gray-300 transition-colors">Recent
                            Notes</span>
                    </div>
                    <div class="space-y-0.5">
                        <a v-for="note in recentNotes" :key="note.title"
                            class="group flex items-center px-2 py-1.5 text-sm rounded-md relative overflow-hidden transition-colors"
                            :class="note.active ? 'bg-white/5 text-primary active-glow' : 'text-gray-400 hover:text-gray-200 hover:bg-white/5'"
                            href="#">
                            <FileText :size="18" class="mr-2 opacity-70" :class="{ 'fill-primary/20': note.active }" />
                            <span class="truncate" :class="{ 'font-medium': note.active }">{{ note.title }}</span>
                            <div v-if="note.active"
                                class="absolute right-2 w-1.5 h-1.5 rounded-full bg-primary shadow-[0_0_8px_rgba(255,191,0,0.8)]">
                            </div>
                        </a>
                    </div>
                </div>

                <!-- Tags -->
                <div>
                    <div class="px-2 mb-2">
                        <span class="text-xs font-medium text-gray-500 uppercase tracking-wider">Tags</span>
                    </div>
                    <div class="flex flex-wrap gap-2 px-2">
                        <span v-for="tag in tags" :key="tag"
                            class="px-2 py-1 rounded-full bg-border-dark text-[11px] text-gray-400 border border-transparent hover:border-gray-600 cursor-pointer">
                            {{ tag }}
                        </span>
                    </div>
                </div>
            </SidebarContent>

            <SidebarFooter
                class="p-3 border-t border-border-light dark:border-border-dark bg-surface-light dark:bg-sidebar-bg">
                <div class="relative group">
                    <span
                        class="absolute inset-y-0 left-0 flex items-center pl-3 text-gray-500 group-focus-within:text-primary transition-colors">
                        <Search :size="16" />
                    </span>
                    <input
                        class="w-full bg-background-light dark:bg-background-dark border border-transparent focus:border-primary/50 text-sm rounded-md py-1.5 pl-9 pr-3 text-gray-800 dark:text-gray-300 placeholder-gray-600 focus:ring-0 transition-all shadow-sm"
                        placeholder="Quick Find..." type="text" />
                    <span class="absolute inset-y-0 right-0 flex items-center pr-2">
                        <kbd
                            class="hidden group-focus-within:hidden px-1.5 py-0.5 text-[10px] font-mono text-gray-500 border border-gray-700 rounded bg-surface-dark">⌘K</kbd>
                    </span>
                </div>
            </SidebarFooter>
        </Sidebar>
    </Sidebar>
</template>
