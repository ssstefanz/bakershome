<template>
    <main id="app">
        <article class="recipe__wrap" v-for="recipe in recipes">
            <h3 class="recipe__title">{{ recipe.title }}</h3>
            <img :src="require('@/assets/' + recipe.image)" :alt="recipe.imgtext" class="recipe__image">

            <p class="recipe__intro">{{ recipe.intro }}</p>
            <div class="recipe__iwrap">
                <h6 class="recipe__subtitle">Ingredients</h6>
                <ul class="recipe__ilist" v-for="ingredient in recipe.ingredients">
                    <li class="recipe__ingredient">{{ ingredient }}</li>
                </ul>
            </div>
            <div class="recipe__stepswrap">
                <h6 class="recipe__subtitle">Instructions</h6>
                <ul class="recipe__steplist" v-for="(instruction, index) in recipe.instructions" >
                    <li class="recipe__step"><span class="recipe__stepnum">Step {{ (index + 1) + ' ' }}</span> <br> {{ instruction }}</li>
                </ul>
            </div>
        </article>
        <article class="recipe__wrap" v-if="nutritionFacts">
            <!-- hidden nutrition facts which link nutrition prop to Nfacts data, toggled with the button -->
            <div class="recipe__hide-wrap" v-if="!show">
                <Nutrition
                    :nutrition="nutritionFacts"
                ></Nutrition>
            </div>
            <div class="recipe__button-wrap">
                <button class="recipe__button" @click="buttonText" ref="buttonToggle">Nutrition Facts</button>
            </div>

        </article>

    </main>
</template>

<script>
import axios from 'axios';
import Nutrition from '@/components/nutrition.vue';
import buttonText from '@/components/mixins.vue';

export default {
    name: 'app',
    components: {
        Nutrition
    },
    mixins: [buttonText],
    data () {
      return {
        // data for the recipes
        loading: true,
        nutritionFacts: null,
        errored: false,
        recipes: [
          {
            title: "Seeded Rye Sourdough Boule",
            image: "bread-2.jpeg",
            imgtext: "a loaf of sourdough bread, photographed from above",
            intro: "A 20% rye flour sourdough loaf, filled with seeds.",
            ingredients: [
                "400 grams bread flour", 
                "100 grams rye flour",
                "375 grams water",
                "100 grams leaven",
                "10g salt"
            ],
            instructions: [
                "Mix 300g warm water and all the leaven in a bowl. When the leaven is incorporated, stir in both flours and mix until all the flour is hydrated. Let rest for about 1 hour in a warm place.",
                "Mix 35g water with 10g salt, stir until incorporated. After the autolyse, add the salt water mixture to the dough and mix thoroughly by hand until the dough has soaked up the salt water and begins to feel smooth and elastic. Cover the bowl and let rest for a half hour in a warm place (about 75 degrees Fahrenheit).",
                "For the next three hours, stretch and fold the dough every half hour. Before the second fold, add the toasted seeds.",
                "When the dough has risen about 25% and feels nicely aerated, gently remove the dough from the ferment container and place on a lightly floured surface. Shape the dough into a boule.",
                "Preheat the oven to 500 degrees Fahrenheit with a dutch oven inside.",
                "When the oven has heated, slide the loaf into the pan, score the top, and bake for 20 minutes.",
                "After 20 minutes, remove the lid and bake uncovered for another 15 to 20 minutes, or until the crust is deep brow.",
                "Remove from pan and let cool before slicing."
            ]
          }
        ]
        }
    },
    mounted () {
        axios
        .post('https://api.edamam.com/api/nutrition-details?app_id=403c0e43&app_key=da5602f91acee1cb56ac0d8c000985ff', {
            title: this.recipes[0].title,
            ingr: this.recipes[0].ingredients
        })
        // .then(response => console.log(response))
        .then(response => this.nutritionFacts = response.data)
        .catch(error => {
            console.error(error)
            this.errored = true 
        })
        .finally(() => this.loading = false)
    },
    head () {
      return {
        titleTemplate: this.recipes[0].title + ' — %s',
        meta: [
          {
            hid: 'description', 
            name: 'description',
            content: this.recipes[0].intro
        }

        ]
      }
    }
}
</script>


