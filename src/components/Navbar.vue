<template>

  <nav class="flex justify-between items-center px-10 pt-7">
    <div @click="isopen = true">
        <img src="/img/menu.png" alt="menu" class="w-[40px] transition-all menubtn">
    </div>

    <div class="relative">
        <input type="checkbox" name="togglemode" id="togglemode" class="absolute w-full h-full opacity-0" @click="mode">
        <img src="/img/contrast.png" alt="sun" class="w-[40px] logotoggle">
    </div>

    <div class="w-screen h-screen absolute bg-[#0000006b] top-0 left-0" :class="isopen ? 'block' : 'hidden' " @click="isopen = false"></div>
    <div class="overflow-hidden h-screen absolute top-0 left-0 bg-white dark:bg-slate-700 font-pupylinux dark:text-white transition-all" :class="isopen ? 'w-[80vw]' : 'w-0' ">
        <p class="text-3xl m-6">TodoKuRi.</p>

        <div class="flex flex-col justify-center items-center h-[60%]">
        <router-link to="/">Home</router-link>
        <router-link to="/about" class="mt-3">About</router-link>
        </div>
    </div>

    </nav>

</template>

<script>
export default {
    data() {
        return {
            test: '',
            isopen : false
        }
    },
    mounted() {
        const html = document.querySelector('html')
        const logotoggle = document.querySelector('.logotoggle')
        const togglemode = document.querySelector('#togglemode')
        const menubtn = document.querySelector('.menubtn')

        if (localStorage.mode) {
            togglemode.checked = true
            if(togglemode.checked){
                html.classList.add('dark')
                logotoggle.src = "/img/crescent-moon.png"
                menubtn.src = "/img/menu-white.png"
            }
        }
    },
    methods: {
        mode(e){
            const html = document.querySelector('html')
            const logotoggle = document.querySelector('.logotoggle')
            const menubtn = document.querySelector('.menubtn')

            if(e.target.checked){
                html.classList.add('dark')
                localStorage.setItem('mode', 'dark')
                logotoggle.src = "/img/crescent-moon.png"
                menubtn.src = "/img/menu-white.png"
            }else{
                html.classList.remove('dark')
                localStorage.removeItem('mode')
                logotoggle.src = "/img/contrast.png"
                menubtn.src = "/img/menu.png"
            }
        }
    },
}
</script>