<script lang="ts">
export const description = "Aether Editor - Vulkan Documentation"
export const iframeHeight = "800px"
</script>

<script setup lang="ts">
import AppSidebar from "@/components/AppSidebar.vue"
import {
    SidebarInset,
    SidebarProvider,
} from "@/components/ui/sidebar"
import {
    Breadcrumb,
    BreadcrumbItem,
    BreadcrumbLink,
    BreadcrumbList,
    BreadcrumbPage,
    BreadcrumbSeparator,
} from "@/components/ui/breadcrumb"
import {
    Tooltip,
    TooltipContent,
    TooltipProvider,
    TooltipTrigger,
} from "@/components/ui/tooltip"
import { Button } from "@/components/ui/button"
import { Separator } from "@/components/ui/separator"
import {
    ChevronRight,
    Edit,
    MoreVertical,
    Calendar,
    Search,
    HelpCircle,
    ArrowRight,
    Copy,
    Link as LinkIcon
} from "lucide-vue-next"
</script>

<template>
    <TooltipProvider>
        <SidebarProvider :style="{
            '--sidebar-width': '350px',
        }">
            <AppSidebar />
            <SidebarInset class="bg-background-light dark:bg-background-dark">
                <header
                    class="h-14 border-b border-border-light dark:border-border-dark flex items-center px-4 md:px-8 justify-between bg-background-light/80 dark:bg-background-dark/80 glass z-10 sticky top-0">
                    <Breadcrumb>
                        <BreadcrumbList class="text-sm text-gray-500 dark:text-gray-400 font-mono">
                            <BreadcrumbItem>
                                <BreadcrumbLink href="#"
                                    class="hover:text-gray-800 dark:hover:text-gray-200 transition-colors">
                                    Arch Linux
                                </BreadcrumbLink>
                            </BreadcrumbItem>
                            <BreadcrumbSeparator>
                                <ChevronRight class="h-4 w-4 opacity-50" />
                            </BreadcrumbSeparator>
                            <BreadcrumbItem>
                                <BreadcrumbPage class="text-primary font-semibold">Vulkan</BreadcrumbPage>
                            </BreadcrumbItem>
                        </BreadcrumbList>
                    </Breadcrumb>
                    <div class="flex items-center space-x-4">
                        <span
                            class="text-xs text-gray-400 dark:text-gray-600 uppercase tracking-widest font-mono hidden sm:inline-block">Read
                            Only</span>
                        <Button variant="ghost" size="icon"
                            class="text-gray-400 hover:text-primary transition-colors h-9 w-9">
                            <Edit class="h-5 w-5" />
                        </Button>
                        <Button variant="ghost" size="icon"
                            class="text-gray-400 hover:text-primary transition-colors h-9 w-9">
                            <MoreVertical class="h-5 w-5" />
                        </Button>
                    </div>
                </header>
                <div class="flex-1 overflow-y-auto relative no-scrollbar">
                    <div
                        class="absolute top-0 left-1/2 -translate-x-1/2 w-[600px] h-[400px] bg-primary/5 rounded-full blur-[100px] pointer-events-none hidden dark:block">
                    </div>
                    <article class="max-w-3xl mx-auto px-6 py-12 md:py-16 prose dark:prose-invert prose-stone">
                        <h1 class="text-4xl md:text-5xl mb-2 !leading-tight tracking-tight relative inline-block">
                            Vulkan
                            <span
                                class="absolute -bottom-2 left-0 w-1/3 h-1 bg-gradient-to-r from-primary to-transparent rounded-full opacity-80"></span>
                        </h1>
                        <p class="text-xl text-gray-500 dark:text-gray-400 font-light mt-6 leading-relaxed">
                            Vulkan and Hardware Acceleration (Intel Xe) configuration guide.
                        </p>
                        <div class="mt-12 group">
                            <h2
                                class="flex items-center text-2xl font-serif text-gray-800 dark:text-gray-100 group-hover:text-primary transition-colors duration-300">
                                <ArrowRight class="mr-2 text-primary opacity-0 group-hover:opacity-100 transition-opacity h-6 w-6 -ml-8" />
                                Vulkan Installation
                            </h2>
                            <p class="text-gray-600 dark:text-gray-400">
                                For Intel Xe graphics (and most modern Intel GPUs), use the <code
                                    class="bg-gray-200 dark:bg-gray-800 text-gray-800 dark:text-primary px-1.5 py-0.5 rounded text-sm font-mono">vulkan-intel</code>
                                driver.
                            </p>
                            <div
                                class="relative mt-4 rounded-lg overflow-hidden border border-border-light dark:border-gray-800 bg-gray-50 dark:bg-[#1E1E1E] shadow-sm">
                                <div
                                    class="flex items-center justify-between px-4 py-2 border-b border-border-light dark:border-gray-800 bg-gray-100/50 dark:bg-[#252525]">
                                    <span class="text-xs text-gray-400 font-mono">bash</span>
                                    <Button variant="ghost" size="icon"
                                        class="h-6 w-6 text-gray-400 hover:text-white transition-colors">
                                        <Copy class="h-4 w-4" />
                                    </Button>
                                </div>
                                <div class="p-4 font-mono text-sm overflow-x-auto">
                                    <span class="text-yellow-600 dark:text-yellow-500">sudo</span> <span
                                        class="text-gray-800 dark:text-gray-300">pacman</span> <span
                                        class="text-blue-600 dark:text-blue-400">-S</span> <span
                                        class="text-gray-600 dark:text-gray-400">vulkan-intel vulkan-icd-loader</span>
                                </div>
                            </div>
                        </div>
                        <div class="mt-10 group">
                            <h2
                                class="flex items-center text-2xl font-serif text-gray-800 dark:text-gray-100 group-hover:text-primary transition-colors duration-300">
                                <ArrowRight class="mr-2 text-primary opacity-0 group-hover:opacity-100 transition-opacity h-6 w-6 -ml-8" />
                                Optional: 32-bit Support
                            </h2>
                            <p class="text-gray-600 dark:text-gray-400">
                                Required for Steam and some Wine/Proton games. Ensure multilib is enabled.
                            </p>
                            <div
                                class="relative mt-4 rounded-lg overflow-hidden border border-border-light dark:border-gray-800 bg-gray-50 dark:bg-[#1E1E1E] shadow-sm">
                                <div
                                    class="flex items-center justify-between px-4 py-2 border-b border-border-light dark:border-gray-800 bg-gray-100/50 dark:bg-[#252525]">
                                    <span class="text-xs text-gray-400 font-mono">bash</span>
                                    <Button variant="ghost" size="icon"
                                        class="h-6 w-6 text-gray-400 hover:text-white transition-colors">
                                        <Copy class="h-4 w-4" />
                                    </Button>
                                </div>
                                <div class="p-4 font-mono text-sm overflow-x-auto">
                                    <span class="text-yellow-600 dark:text-yellow-500">sudo</span> <span
                                        class="text-gray-800 dark:text-gray-300">pacman</span> <span
                                        class="text-blue-600 dark:text-blue-400">-S</span> <span
                                        class="text-gray-600 dark:text-gray-400">lib32-vulkan-intel
                                        lib32-vulkan-icd-loader</span>
                                </div>
                            </div>
                        </div>
                        <div class="mt-10 group">
                            <h2
                                class="flex items-center text-2xl font-serif text-gray-800 dark:text-gray-100 group-hover:text-primary transition-colors duration-300">
                                <ArrowRight class="mr-2 text-primary opacity-0 group-hover:opacity-100 transition-opacity h-6 w-6 -ml-8" />
                                Verification
                            </h2>
                            <p class="text-gray-600 dark:text-gray-400">
                                Install <code
                                    class="bg-gray-200 dark:bg-gray-800 text-gray-800 dark:text-primary px-1.5 py-0.5 rounded text-sm font-mono">vulkan-tools</code>
                                to verify the installation integrity.
                            </p>
                            <div
                                class="relative mt-4 rounded-lg overflow-hidden border border-border-light dark:border-gray-800 bg-gray-50 dark:bg-[#1E1E1E] shadow-sm">
                                <div
                                    class="flex items-center justify-between px-4 py-2 border-b border-border-light dark:border-gray-800 bg-gray-100/50 dark:bg-[#252525]">
                                    <span class="text-xs text-gray-400 font-mono">bash</span>
                                    <Button variant="ghost" size="icon"
                                        class="h-6 w-6 text-gray-400 hover:text-white transition-colors">
                                        <Copy class="h-4 w-4" />
                                    </Button>
                                </div>
                                <div class="p-4 font-mono text-sm overflow-x-auto">
                                    <div class="mb-1"><span class="text-yellow-600 dark:text-yellow-500">sudo</span>
                                        <span class="text-gray-800 dark:text-gray-300">pacman</span> <span
                                            class="text-blue-600 dark:text-blue-400">-S</span> <span
                                            class="text-gray-600 dark:text-gray-400">vulkan-tools</span>
                                    </div>
                                    <div><span class="text-purple-600 dark:text-purple-400">vulkaninfo</span> | <span
                                            class="text-yellow-600 dark:text-yellow-500">grep</span> <span
                                            class="text-green-600 dark:text-green-400">"deviceType"</span></div>
                                </div>
                            </div>
                        </div>
                        <Separator class="my-12 bg-border-light dark:bg-gray-800" />
                        <div class="mt-10 group">
                            <h2
                                class="flex items-center text-2xl font-serif text-gray-800 dark:text-gray-100 group-hover:text-primary transition-colors duration-300">
                                <ArrowRight class="mr-2 text-primary opacity-0 group-hover:opacity-100 transition-opacity h-6 w-6 -ml-8" />
                                Hardware Acceleration (VA-API)
                            </h2>
                            <p class="text-gray-600 dark:text-gray-400">
                                Intel Xe graphics use the <code
                                    class="bg-gray-200 dark:bg-gray-800 text-gray-800 dark:text-primary px-1.5 py-0.5 rounded text-sm font-mono">intel-media-driver</code>
                                for hardware-accelerated video decoding/encoding.
                            </p>
                            <div
                                class="relative mt-4 rounded-lg overflow-hidden border border-border-light dark:border-gray-800 bg-gray-50 dark:bg-[#1E1E1E] shadow-sm">
                                <div
                                    class="flex items-center justify-between px-4 py-2 border-b border-border-light dark:border-gray-800 bg-gray-100/50 dark:bg-[#252525]">
                                    <span class="text-xs text-gray-400 font-mono">bash</span>
                                    <Button variant="ghost" size="icon"
                                        class="h-6 w-6 text-gray-400 hover:text-white transition-colors">
                                        <Copy class="h-4 w-4" />
                                    </Button>
                                </div>
                                <div class="p-4 font-mono text-sm overflow-x-auto">
                                    <span class="text-yellow-600 dark:text-yellow-500">sudo</span> <span
                                        class="text-gray-800 dark:text-gray-300">pacman</span> <span
                                        class="text-blue-600 dark:text-blue-400">-S</span> <span
                                        class="text-gray-600 dark:text-gray-400">intel-media-driver libva-utils</span>
                                </div>
                            </div>
                        </div>
                        <div
                            class="mt-20 pt-6 border-t border-border-light dark:border-gray-800 flex justify-between text-xs text-gray-400 font-mono">
                            <div class="flex space-x-4">
                                <Button variant="link" size="sm"
                                    class="h-auto p-0 text-gray-400 hover:text-primary transition-colors">
                                    0 backlinks
                                </Button>
                                <Button variant="link" size="sm"
                                    class="h-auto p-0 text-gray-400 hover:text-primary transition-colors">
                                    183 words
                                </Button>
                                <span>1,354 characters</span>
                            </div>
                            <div>
                                Last edited: <span class="text-gray-500 dark:text-gray-300">Today at 10:42 AM</span>
                            </div>
                        </div>
                    </article>
                    <div class="h-20"></div>
                </div>
            </SidebarInset>
            <aside
                class="hidden xl:flex w-14 border-l border-border-light dark:border-border-dark flex-col items-center py-4 bg-surface-light dark:bg-surface-dark z-20">
                <Tooltip>
                    <TooltipTrigger as-child>
                        <Button variant="ghost" size="icon"
                            class="p-2 mb-4 text-gray-400 hover:text-primary transition-colors h-10 w-10">
                            <Calendar class="h-6 w-6" />
                        </Button>
                    </TooltipTrigger>
                    <TooltipContent side="left" class="bg-gray-800 text-white text-xs px-2 py-1 rounded">
                        Calendar
                    </TooltipContent>
                </Tooltip>
                <Tooltip>
                    <TooltipTrigger as-child>
                        <Button variant="ghost" size="icon"
                            class="p-2 mb-4 text-gray-400 hover:text-primary transition-colors h-10 w-10">
                            <Search class="h-6 w-6" />
                        </Button>
                    </TooltipTrigger>
                    <TooltipContent side="left" class="bg-gray-800 text-white text-xs px-2 py-1 rounded">
                        Search
                    </TooltipContent>
                </Tooltip>
                <div class="flex-1"></div>
                <Tooltip>
                    <TooltipTrigger as-child>
                        <Button variant="ghost" size="icon"
                            class="p-2 mt-4 text-gray-400 hover:text-primary transition-colors h-10 w-10">
                            <HelpCircle class="h-6 w-6" />
                        </Button>
                    </TooltipTrigger>
                    <TooltipContent side="left" class="bg-gray-800 text-white text-xs px-2 py-1 rounded">
                        Help
                    </TooltipContent>
                </Tooltip>
            </aside>
        </SidebarProvider>
    </TooltipProvider>
</template>
