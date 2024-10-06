<template>


    <a href="/fields/Fotehobod">
        <div class="p-2 rounded-xl flex items-start space-x-4 border-2 myborder hover:shadow-xl cursor-pointer me-3 my-2">
            <img :src="`${images}/nth/0/`" height="220" class="rounded-xl" width="274" alt="">
            <div class="space-y-6">
                <h2 class="font-bold text-xl text-start my-4">{{ title }}</h2>
                <div class="flex space-x-3">
                    <button class="myGreen1 p-2 rounded-lg">
                        <img src="../assets/carrot.svg" alt="">
                    </button>
                    <button class="myGreen2 p-2 rounded-lg">
                        <img src="../assets/Vector (1).svg" alt="">
                    </button>
                    <button class="myGreen2 p-2 rounded-lg">
                        <img src="../assets/Group 1171279512.svg" alt="">
                    </button>
                </div>
    
                <div class="flex items-center space-x-2">
                    <img src="../assets/location.svg" alt="">
                    <span>{{ location }}</span>
                </div>
    
                <p style="max-width: 260px;" class="text-start">
                    {{ description }}
                </p>
    
            </div>
    
           
    
        </div>
    </a>


</template>

<script>

    export default {
        props: ['title','description', 'location', 'images']
    }
</script>