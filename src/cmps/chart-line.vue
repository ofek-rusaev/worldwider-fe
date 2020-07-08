<script>
import { Line } from "vue-chartjs";

export default {
  extends: Line,
  props: {
    data: {},
    lables: {}
  },
  data() {
    return {
      chartdata: {
        labels: [
          "Mar 19",
          "Apr 19",
          "May 19",
          "Jun 19",
          "July 19",
          "Aug 19",
          "Sep 19",
          "Oct 19",
          "Nov 19",
          "Dec 19",
          "Jan 20",
          "Feb 20",
          "Mar 20"
        ],
        datasets: [
          {
            label: "Total Reservations (Attendees)",
            backgroundColor: "#023d96",
            data: [20, 30, 60, 20, 40, 10, 10, 20, 30, 60, 20, 60, 90, 10]
          },
          {
            label: "Total Reservations (Income)",
            backgroundColor: " #548eb3",
            data: [
              1000,
              230,
              1500,
              980,
              800,
              1200,
              500,
              1000,
              230,
              1500,
              980,
              800,
              1200,
              500
            ]
          }
        ]
      },
      options: {
        responsive: true,
        maintainAspectRatio: false
      }
    };
  },

  mounted() {
    this.renderChart(this.chartdata, this.options);
  }
};
</script>
