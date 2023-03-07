<script>
export default {
    data () {
        return{
            show: true
        }
    },
    methods: {
      // button to show/hide recipes and change the button text
      buttonText: function (first='show', second='hide') {
        this.show = !this.show;
        console.log(first);
        this.$refs.buttonToggle.innerText = this.show?first:second;
      }
    }
}
</script>