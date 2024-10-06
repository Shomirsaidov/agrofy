<template>

    <TopBar/>

    <div class="px-40 pt-4">
        <div class="flex space-x-3">
    
            <div class="space-y-8" style="width: 350px;">
                <div class="border-2 myGreen4 text-white font-black p-4 rounded-lg border-green-700">
                    + New question
                </div>
                <div class="border-2 rounded-lg p-3 myGreen4 text-white border-green-700">
                    <h2 class="text-xl font-bold text-start">List of quesions</h2>
                    <div class="mt-8 space-y-3">
                        <div class="text-start border-t-2 pt-2 border-white">
                            <p>What are the best practices for managing soil moisture during a prolonged drought?</p>
                            <p class="text-xs">08 Oct</p>
                        </div>
                        <div class="text-start border-t-2 pt-2 border-white">
                            <p>How can I use satellite data to monitor crop health on my farm?</p>
                            <p class="text-xs">08 Oct</p>
                        </div>
                        <div class="text-start border-t-2 pt-2 border-white">
                            <p>What are common early signs of pest infestation, and how can I detect them using remote sensing data?</p>
                            <p class="text-xs">08 Oct</p>
                        </div>
                        <div class="text-start border-t-2 pt-2 border-white">
                            <p>Which NASA satellite data is most useful for tracking soil moisture levels?</p>
                            <p class="text-xs">08 Oct</p>
                        </div>
                        <div class="text-start border-t-2 pt-2 border-white">
                            <p>What should I do if I detect an anomaly in my farm’s NDVI data?</p>
                            <p class="text-xs">08 Oct</p>
                        </div>
                    </div>
                    
                    
                </div>
            </div>
            <div class="flex flex-col border-4 rounded-xl w-full border-green-700 p-3 " style="position: relative; max-height: 85vh; overflow-y: scroll;">
                <div class="flex-1">
                    
                    <div class="message flex items-start space-x-4">
                        <img src="../assets/images (1).jpeg" class="rounded-full" style="width: 60px; height: 60px;" alt="">
                        <div class="myGreen4 text-white p-2 rounded-lg text-start">What are the most effective ways to prevent crop diseases in a humid climate?</div>
                    </div>

                    <hr class="my-8">

                    <div>
                        <h3 class="text-xl font-bold">Answers</h3>

                        <div class="message flex flex-row-reverse items-start my-6">
                            <img src="../assets/profile-circle.svg" class="rounded-full" style="width: 40px; height: 40px;" alt="">
                            <div class="bg-gray-300  p-2 rounded-lg m-4 text-start">Regularly rotate crops to prevent the buildup of soil-borne pathogens, and ensure good airflow between plants to reduce moisture accumulation, which can promote disease.</div>
                        </div>

                        <div class="message flex flex-row-reverse items-start my-6">
                            <img src="../assets/profile-circle.svg" class="rounded-full" style="width: 40px; height: 40px;" alt="">
                            <div class="bg-gray-300  p-2 rounded-lg m-4 text-start">Use disease-resistant seed varieties and consider implementing integrated pest management (IPM) strategies that include biological controls to minimize disease risks.</div>
                        </div>

                        <div class="message flex flex-row-reverse items-start my-6">
                            <img src="../assets/profile-circle.svg" class="rounded-full" style="width: 40px; height: 40px;" alt="">
                            <div class="bg-gray-300  p-2 rounded-lg m-4 text-start">Monitor soil moisture levels closely using remote sensing data to avoid over-irrigation, as excess moisture can encourage the growth of fungi and other pathogens.</div>
                        </div>
                        
                    </div>



                </div>                

            </div>
            

        </div>

        <div class="flex justify-center mb-16 mt-10 ">
            <div class="border-2 w-1/4 rounded-lg shadow-xl p-10 space-y-3">

                <h3 class="text-xl font-bold">Help to Falonchi...</h3>
                <textarea type="text" class="border-2 border-green-600 outline-none p-4 rounded-3xl" placeholder="your advice..." style=""></textarea>
                <button class="p-4 w-full myGreen4 text-white font-bold rounded-lg">Send</button>

            </div>
        </div>


    </div>

</template>


<script>

    import TopBar from '../components/TopBar.vue';

    export default {
        name: 'Forum',
        components: {
            TopBar
        }
    }

</script>
