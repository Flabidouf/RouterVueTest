<script setup>
    import { useRoute,useRouter, RouterView } from 'vue-router'
    import cars from "../data/cars.json"


    const route = useRoute(); // useRoute() permet d'accéder aux paramètres/infos de la route 
    const router = useRouter(); // useRouter() permet d'accéder aux méthodes de navigation

    const carId = parseInt(route.params.id);

    const showContact = () => {
        if(carId=== 4) return;
        return router.push(`/cars/${carId}/contact`)
    }

    const car = cars.find(c => c.id === carId );
    
</script>


<template>
    <div v-if="car">
        <h1>Car View</h1>
        <p>{{ car.name }}</p> 
        <p>{{ car.year }}</p>
        <p>{{ car.price }}</p>
        <button @click="showContact">Click for contact</button>
        <RouterView />  <!-- RouterView va automatiquement checker les children de la route -->
    </div>
    <div v-else>
        <h1>Car not found</h1>
    </div>
</template>

