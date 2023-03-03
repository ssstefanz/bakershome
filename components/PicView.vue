<!-- picture component built with props -->
<template>
    <b-carousel-slide 
        class="picture" 
        :img-src="require('@/assets/' + picture)" 
    >
        <h5>{{ imgTitle }}</h5>
    </b-carousel-slide>
</template>
    
<script>


export default {
    name: 'pictureView',
    // props with validation
    props: {
        picture: {
            type: String,
            required: true
        },
        altText: {
            type: String
        },
        imgTitle: {
            type: String
        }
    }
};

</script>