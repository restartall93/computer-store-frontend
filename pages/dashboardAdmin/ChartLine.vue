<script>
import {Line} from 'vue-chartjs';
export default{
    extends: Line,
    props: ["chartData"],
    mounted(){
        this.init()
    },
    watch: {
        chartData () {
            this.init()
        }
    },
    methods: {
        init(){
            this.renderChart(
                {
                    labels: this.getLabel(),
                    datasets: [
                        {
                            label: 'Number booking',
                            data: this.chartData,
                            backgroundColor: 'transparent',
                            borderColor: '#17A2B8',
                            pointBackgroundColor: '#DC3545'
                        }
                    ]
                },
                {
                    responsive: true,
                    maintainAspectRatio: false,
                    title: {
                        display: true,
                        text: 'NUMBER BOOKING IN 7 DAYS'
                    }
                }
            )
        },
        getLabel () {
            var labelChartLines = []
            for (var i = 0; i < this.chartData.length; i++) {
                var day = new Date()
                day.setDate(day.getDate() - (this.chartData.length - i))
                labelChartLines[i] = day.getDate() + '/' + day.getMonth()
            }
            return labelChartLines
        }       
    }
};
</script>
