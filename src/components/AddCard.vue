<template>

    <div @click="navigate('/new-field')" class="myGreen3 flex justify-center items-center me-4 my-2 hover:border-4 cursor-pointer border-green-600  rounded-xl" style="width: 570px;">
        <img src="../assets/add.svg" alt="">
    </div>

</template>


<script>

    export default {
        methods: {
            navigate(to) {
                this.$router.push(to)
            }
        }
    }

</script>