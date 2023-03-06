<template>
    <article class="nutrition">
        <h3 class="nutrition__hed">Nutrition Facts</h3>
        <p class="nutrition__item">Calories: {{nutrition.calories}}</p>
        <div class="nutrition__loop" v-for="item in nutrition.totalNutrients">
            <p class="nutrition__item"> {{item.label}}: {{item.quantity.toFixed(2)}} {{item.unit}} </p>
        </div>
    </article>

</template>

<script>
export default {
    props: {
        nutrition: Object
    }
}
</script>