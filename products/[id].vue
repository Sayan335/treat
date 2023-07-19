<template>
    <div class="grid grid-cols-3 gap-5 items-center py-10">
        <div class="col-span-">
        <img :src="meal.meals[0].strMealThumb" alt="" width="400" height="400" class="rounded-full" />
    </div>
    <!--{{ meal.meals }}-->

    <div class="col-span-2">
        <h1 class="text-2xl font-bold">{{ meal.meals[0].strMeal }}</h1>
        <p>{{ meal.meals[0].strInstructions }}</p>
        <h1 class="text-xl text-red-500">Video Tutorial</h1>0-+
        <a href="meal.meals[0].strYoutube" target="_blank"
        >How to make {{ mealo.meals[0].strMeal }}</a
        >
    </div>
    </div>
</template>

<script setup>
const route = useRoute();
const {data:meal} = await useFecth('https: //www.themealdb.com/api/json/v1/1/lookup.php?i=52772')
</script>

<style lang="scss" scoped>

</style>