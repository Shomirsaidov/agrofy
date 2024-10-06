<template>


    <TopBar/>

    <div class="px-20 py-16 flex justify-center">
        <div class="flex justify-center flex-wrap">
            <AddCard/>
            <FieldCard/>
            <FieldCard/>
            <FieldCard/>
            <FieldCard/>
            <FieldCard/>
            <FieldCard/>
    
        </div>
    </div>





</template>


<script>

    import FieldCard from '../components/FieldCard.vue'
    import TopBar from '@/components/TopBar.vue'
    import AddCard from '@/components/AddCard.vue'


    export default {
        components: {
            FieldCard, TopBar, AddCard
        }
    }
    
</script>