<template>

    <div class="flex justify-center rounded-lg px-40 sticky sticky-top top-2" style="background: transparent; z-index: 9;">
        <div class="flex justify-between items-center border-2 shadow-lg p-4 rounded-3xl mt-2 w-full bg-white">
            <img src="../assets/nasa_logo.png" alt="">
            <div class="flex items-center text-xl space-x-16 text-green-500 font-bold " >
                <router-link to="/my-fields">My fields</router-link> 
                <router-link to="/notifications">Notifications</router-link>
                <router-link to="/forum">Community</router-link>
                <router-link to="/">About us</router-link>
                <router-link to="/login">Log in</router-link>
            </div>
            <div class="flex items-center space-x-3">
                <img src="../assets/tabler_notification.svg" alt="">
                <img src="../assets/images (1).jpeg" width="50" class="rounded-full" style="width: 50px; height: 50px;" alt="">
            </div>
        </div>
    </div>


    

</template>

<style>



</style>