<template>


    <TopBar/>

    <div class="poster1 p-20 mt-8">
        <div class="flex justify-between">
            <div class="flex justify-start flex-col items-start space-y-10">
                <h1 class="text-start text-white font-black text-4xl">Agroconnect <br> explore, be aware, analyze, predict your land.</h1>
                <button class="text-start p-16 py-4 hover:border-4 border-green-500 rounded-full bg-white text-my text-xl font-black">Register</button>
            </div>
            <div class="space-y-10 flex justify-end pe-40">
                <div class="w-1/2 text-start text-white font-bold">Empowering farmers with real-time insights and actionable recommendations using NASA data and AI to optimize crop health and productivity.</div>
            </div>
        </div>
        <div class="flex justify-end">
            <div class="myGreen1" style="width: 200px;">
                <div class="text-2xl font-bold">Agrofy</div>
            </div>
        </div>
    </div>


    <div class="px-20 py-16">
        <h2 class="text-start text-4xl font-bold text-my mb-8">Our soft</h2>
        <div class="flex space-x-3">
            <div class="hover:shadow-xl cursor-pointer rounded-xl mygradient border myborder">
                <div class="flex justify-center">
                    <img src="../assets/earth_land.png" class="border rounded-full border-white mt-16" width="150" alt="">
                </div>
                <h2 class="text-3xl my-6  font-bold ">Explains</h2>
                <div class="flex justify-center">
                    <div class="w-3/4 text-start font-bold mb-16">Grasping MODIS and SAMP datasets from nasa will be a breeze with us</div>
                </div>
            </div>
            <div class="hover:shadow-xl cursor-pointer rounded-xl mygradient border myborder">
                <div class="flex justify-center">
                    <img src="../assets/earth_land.png" class="border rounded-full border-white mt-16" width="150" alt="">
                </div>
                <h2 class="text-3xl my-6  font-bold ">Predicts</h2>
                <div class="flex justify-center">
                    <div class="w-3/4 text-start font-bold mb-16">We built a predictive model of precipitations and crops quality </div>
                </div>
            </div>
            <div class="hover:shadow-xl cursor-pointer rounded-xl mygradient border myborder">
                <div class="flex justify-center">
                    <img src="../assets/earth_land.png" class="border rounded-full border-white mt-16" width="150" alt="">
                </div>
                <h2 class="text-3xl my-6  font-bold ">Recommends</h2>
                <div class="flex justify-center">
                    <div class="w-3/4 text-start font-bold mb-16">What to do next ? Based on data AI gives useful insights for you </div>
                </div>
            </div>
            <div class="hover:shadow-xl cursor-pointer rounded-xl mygradient border myborder">
                <div class="flex justify-center">
                    <img src="../assets/earth_land.png" class="border rounded-full border-white mt-16" width="150" alt="">
                </div>
                <h2 class="text-3xl my-6  font-bold ">Notifies</h2>
                <div class="flex justify-center">
                    <div class="w-3/4 text-start font-bold mb-16">Face and be ready for any natural adversity being notified about it</div>
                </div>
            </div>
        </div>

        

    </div>


    <div class="poster2 px-40">
        <h2 class="text-start text-3xl font-bold text-my mb-8">Summary</h2>
        <p class="w-1/2 text-lg text-start">Leverage the power of NASA’s Earth Observation data combined with advanced machine learning to provide farmers with a comprehensive view of their farm’s current condition. Our solution predicts and alerts about potential issues like droughts, pests, and nutrient deficiencies, while offering tailored recommendations for optimizing crop health and boosting yields. Simplifying agricultural decision-making with accurate, data-driven insights.</p>
        <br>    
        <p class="w-1/2 text-lg text-start">Utilizing NASA’s Earth Observation data and machine learning, our solution provides farmers with real-time insights into crop health, predicts potential issues, and offers actionable recommendations. From detecting drought risks to optimizing soil health, we simplify decision-making for farmers with accurate, data-driven information to enhance productivity.</p>


    </div>

    <div class="flex justify-between space-x-16 px-40">
        <div class="comics_bg rounded-3xl p-16 px-32">
            <h1 class="text-4xl font-bold mt-10">Our comics</h1>
            <div class="flex justify-center">
                <img src="../assets/comics.png" class="my-8" width="200" height="200" style="width: 200px; height: 200px" alt="">
            </div>

            <div>
                <a href="/Agrocolypse.pdf">
                    <button class="p-4 px-16 bg-yellow-400 text-white rounded-full text-2xl">Read</button>
                </a>
            </div>
        </div>

        <div class="comics_bg rounded-3xl p-16 px-32">
            <h1 class="text-4xl font-bold mt-10">Our game</h1>
            <div class="flex justify-center">
                <img src="../assets/a_pixel_logo_for_fieldify_an_agricultural_themed_g_HSl6jkHBRpunYqnKikZQDw.jpeg" class="my-8" width="200" height="200" style="width: 200px; height: 200px" alt="">
            </div>
            <button class="p-4 px-16 bg-red-600 text-white rounded-full text-2xl">Play</button>
        </div>
    </div>


    

    <div>
        <h3 class="text-my text-4xl font-black mt-16">Our partners</h3>
        <div class="flex justify-center my-16">
            <img src="../assets/nasa+firan.png" width="370" alt="">
        </div>
    </div>


</template>


<style>
@import url('../assets/styles/landing');

</style>

<script>

    
import TopBar from '../components/TopBar.vue';

export default {
    name: 'Landing',
    components: {
        TopBar
    }
}


</script>