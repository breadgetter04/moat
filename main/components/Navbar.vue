<template>
    <nav
        class="sticky top-4 z-50 w-2/3 mx-auto backdrop-blur-lg border border-white/60 rounded-3xl py-3 px-6 shadow-xl flex justify-center">
        <div class="relative flex items-center justify-between w-full">
            <button class="flex flex-row text-xl font-semibold text-black transition-all duration-200 ml-10"
                @click="scrollToSection('top')">
                <!--<img src="" alt="Logo" class="w-8 h-8 object-contain mr-2" />-->
                <div class="text-2xl font-medium">moat</div>
            </button>
            <!-- Center: Nav Items -->
            <nav
                class="hidden xl:flex absolute left-1/2 top-1/2 transform -translate-x-1/2 -translate-y-1/2 space-x-8 text-black transition-all duration-200">
                <template v-for="item in navItems" :key="item.text">
                    <button @click="handleNavClick(item.id)" class="nav-link">
                        {{ item.text }}
                    </button>
                </template>
            </nav>
            <!-- Right: CTA -->
            <div class="flex-1 flex justify-end items-center mr-4 lg:mr-0">
                <div class="hidden xl:block">
                    <Button @click="goToPage" label="Click To Upload" />
                </div>
                <!-- Mobile Toggle -->
                <button @click="toggleMobile" class="xl:hidden flex flex-col justify-between w-6 h-5 z-50 ml-4"
                    :class="{ 'open': mobileOpen }" :aria-label="mobileOpen ? 'Close menu' : 'Open menu'"
                    :aria-expanded="mobileOpen">
                    <span class="hamburger-line" />
                    <span class="hamburger-line" />
                    <span class="hamburger-line" />
                </button>
            </div>
        </div>
        <!-- Mobile Dropdown -->
        <transition name="mobile-menu">
            <div v-if="mobileOpen" class="xl:hidden mt-10 space-y-1 text-center">
                <template v-for="item in navItems" :key="item.text">
                    <button @click="() => { handleNavClick(item.id); mobileOpen = false }"
                        class="nav-link block w-full py-1">
                        {{ item.text }}
                    </button>
                </template>
                <div class="pt-1">
                    <Button label="" />
                </div>
            </div>
        </transition>
    </nav>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { useRoute, useRouter } from 'vue-router'

const route = useRoute();
const router = useRouter();
const isHome = computed(() => route.path === '/');

const goToPage = () => {
    if (!user.value) {
        router.push('/')
    } else {
        router.push('/')
    }
}



const navItems = [
    { text: 'Product', id: '#' },
    { text: 'Resources', id: '#' },
    { text: 'Pricing', id: '#' },
    { text: 'Blog', id: '#' },
    { text: 'Contact', id: '#' }
]

const scrollToSection = async (id) => {
    if (isHome.value) {
        // Already on homepage → scroll directly
        const el = document.getElementById(id)
        if (el) {
            window.scrollTo({
                top: el.offsetTop - 40,
                behavior: 'smooth',
            })
        }
    } else {
        // Not on homepage → navigate, then scroll
        await router.push('/#' + id)
        // Wait for DOM to update (short delay)
        setTimeout(() => {
            const el = document.getElementById(id)
            if (el) {
                window.scrollTo({
                    top: el.offsetTop - 40,
                    behavior: 'smooth',
                })
            }
        }, 300)
    }
    mobileOpen.value = false
}

const handleNavClick = (id) => {
    if (id === '#') {
        router.push('/account')
        mobileOpen.value = false
        return
    }
    scrollToSection(id)
}


const isScrolled = ref(false)
const mobileOpen = ref(false)

const handleScroll = () => {
    isScrolled.value = window.scrollY > 50
}

const toggleMobile = () => {
    mobileOpen.value = !mobileOpen.value
}
onMounted(() => {
    window.addEventListener('scroll', handleScroll)
})
onUnmounted(() => {
    window.removeEventListener('scroll', handleScroll)
})
</script>

<style scoped>
/* Consolidated navigation link styles */
.nav-link {
    color: #052e16;
    font-weight: 500;
    transition: all 0.2s cubic-bezier(0.4, 0, 0.2, 1);
    padding: 0.25rem 0.5rem;
    border-radius: 0.375rem;
    outline: none;
}

.nav-link:hover {
    color: teal-400;
    transform: scale(1.1);
}

/* Better mobile menu transitions */
.mobile-menu-enter-active {
    transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

.mobile-menu-leave-active {
    transition: all 0.2s cubic-bezier(0.4, 0, 0.2, 1);
}

.mobile-menu-enter-from {
    opacity: 0;
    transform: translateY(-15px) scale(0.95);
}

.mobile-menu-leave-to {
    opacity: 0;
    transform: translateY(-10px) scale(0.98);
}

/* Hamburger menu styles */
.hamburger-line {
    display: block;
    width: 100%;
    height: 3px;
    background-color: #052e16;
    /* green-950 equivalent */
    transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
    border-radius: 2px;
}

/* When mobileOpen is true, animate to X */
.open .hamburger-line:nth-child(1) {
    transform: translateY(8px) rotate(45deg);
}

.open .hamburger-line:nth-child(2) {
    opacity: 0;
}

.open .hamburger-line:nth-child(3) {
    transform: translateY(-8px) rotate(-45deg);
}

html {
    scroll-behavior: smooth;
}
</style>