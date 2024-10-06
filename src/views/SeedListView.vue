<template>
    <TopBar/>
    <div class="px-40">
        <div class="flex my-6 space-x-4 ">
            <div class="border-4 myborder rounded-2xl py-16 px-10">
                <img src="../assets/potato.png" alt="">
            </div>
            <div class="border-4 myborder rounded-2xl py-16 px-10">
                <img src="../assets/tomato.png" alt="">
            </div>
            <div class="border-4 myborder rounded-2xl py-16 px-10">
                <img src="../assets/potato.png" alt="">
            </div>
            <div class="border-4 myborder rounded-2xl py-16 px-10">
                <img src="../assets/potato.png" alt="">
            </div>
        </div>

        <div class="flex my-6 space-x-4 ">
            <div class="border-4 myborder rounded-2xl py-16 px-10">
                <img src="../assets/potato.png" alt="">
            </div>
            <div class="border-4 myborder rounded-2xl py-16 px-10">
                <img src="../assets/tomato.png" alt="">
            </div>
            <div class="border-4 myborder rounded-2xl py-16 px-10">
                <img src="../assets/potato.png" alt="">
            </div>
            <div class="border-4 myborder rounded-2xl py-16 px-10">
                <img src="../assets/potato.png" alt="">
            </div>
        </div>

        <button class="p-4 w-full myGreen4 text-white font-bold rounded-lg my-8">
            Submit
        </button>

    </div>

</template>


<script>

    
import TopBar from '../components/TopBar.vue';

export default {
    name: 'Landing',
    components: {
        TopBar
    }
}


</script>