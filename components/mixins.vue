<script>
export default {
    data () {
        return{
            show: true
        }
    },
    methods: {
      // button to show/hide recipes and change the button text
      buttonText: function () {
        this.show = !this.show;
        this.$refs.buttonToggle.innerText = this.show?"See More":"Hide";
      }
    }
}
</script>