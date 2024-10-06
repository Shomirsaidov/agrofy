<template>


    <TopBar/>

    <div class="px-20 py-16 flex justify-center">
        <div class="flex justify-center flex-wrap">
            <AddCard/>



            <FieldCard v-for="field in fields" :title="field.title" :description="field.description"  :images="field.images" :location="field.longitude + field.latitude"/>
           
    
        </div>
    </div>





</template>


<script>

    import FieldCard from '../components/FieldCard.vue'
    import TopBar from '@/components/TopBar.vue'
    import AddCard from '@/components/AddCard.vue'

    import axios from 'axios';


    export default {
        data: () => ({
            fields: null
        }),
        components: {
            FieldCard, TopBar, AddCard
        },
        async mounted() {
            await axios.get('https://agrofy-app-gsghy.ondigitalocean.app/api/v1/my-fields')
                .then(resp => {
                    this.fields = resp.data
                    console.log(resp.data);
                })
                .catch(e => {
                    console.log(e);
                })
        }
    }
    
</script>