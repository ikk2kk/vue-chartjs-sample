<script>
import{ Bar, mixins } from 'vue-chartjs'

export default {
    mixins: [mixins.reactiveProp],
    props: ['chartData', 'options'],
    extends: Bar,
    mounted(){
        this.renderChart(this.chartData, this.options)
    },
}
</script>