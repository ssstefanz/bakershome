<template>
    <div class="recipe__button-wrap">
        <button v-if="!showSecondText" class="recipe__button" @click="showSecondText=true" ref="buttonToggle">{{ InitialText }}</button>
        <button v-if="showSecondText" class="recipe__button" @click="showSecondText=false" ref="buttonToggle">{{ SecondText }}</button>
    </div>
</template>

<script>
    export default {

    props: {
        InitialText: String,
        SecondText: String
    },
        data () {
        return {
            showSecondText: false
        }
    }
 }
</script>