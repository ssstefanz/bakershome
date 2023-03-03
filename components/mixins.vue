<script>
//toggle mixin
export default {
    data() {
        return {
            isActive: false
        }
    },
    methods: {
        toggleShow() {
            this.isActive = !this.isActive;
        }
    }
};
</script>