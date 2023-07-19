<template>
<div>
    <section v-if="pending">
        <h1>loading...</h1>
    </section>
    <section v-else>
        <select class="form-select" aria-label="Default select example" v-model="name" @click="getUrl(name)">
            <option selected>Open this select menu</option>
            <option value="1">one</option>
            <option :value="category.strCategory" v-for="(category,index) in categoryData.categories" :key="index">{{ category.strCategory }}</option>
          
        </select>
        <div class="container ms-auto grid grid-cols-3 gap-4 m-4">
            <div v-for="(p, index) in data.meals" :key="index">
                <nuxt-link :to="`products/${p.idMeal}`">
                    <productcard-component :product="p" />
                </nuxt-link>

            </div>
        </div>
    </section>
</div>
</template>

<script setup>
let name = "";
const url = ref(`https://www.themealdb.com/api/json/v1/1/filter.php?c=Seafood`)
const {data: categoryData} = await useFetch("https://www.themealdb.com/api/json/v1/1/categories.php");
  const {data, pending} =await useFetch(url, {refetch:true});

  function getUrl(category){
    url.value=`https://www.themealdb.com/api/json/v1/1/filter.php?c=${category}`
  }
</script>

<style  scoped>

</style>
