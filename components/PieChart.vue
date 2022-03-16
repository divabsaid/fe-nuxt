
<script>
import { Pie } from 'vue-chartjs'

export default {
  extends: Pie,
  props: {
    data: {
      type: Object,
      required: true
    }
  },
  mounted () {
    this.renderChart(this.data, {
      responsive: true,
      maintainAspectRatio: true
    })
  }
}
</script>
