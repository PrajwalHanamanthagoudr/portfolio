<template>
  <div style="width: 600px; height: 600px;">
    <canvas  ref="skillChart"></canvas>
  </div>
</template>

<script>
import { Chart } from 'chart.js/auto';

export default {
  data() {
    return {
      chart: null,
    };
  },
  mounted() {
    this.renderChart();
  },
  methods: {
    renderChart() {
      const ctx = this.$refs.skillChart.getContext('2d');
      this.chart = new Chart(ctx, {
        type: 'bar',
        data: {
          labels: [
            'HTML',
            'CSS',
            'JS',
            'Vue.js',
            'Tailwind',
            'Git',
            'Java',
            'Node.js',
            'SQL',
            'Postman',
            'JDBC',
            'Hibernate',
          ],
          datasets: [
            {
              label: 'Skill Level',
              backgroundColor: [
                '#E44D26', // HTML color
                '#2965F1', // CSS color
                '#F0DB4F', // JS color
                '#41B883', // Vue.js color
                '#38B2AC', // Tailwind color
                '#F1502F', // Git color
                '#007396', // Java color
                '#8CC84B', // Node.js color
                '#336791', // SQL color
                '#EF5B25', // Postman color
                '#000',    // JDBC color
                '#4A90E2', // Hibernate color
              ],
              borderWidth: 1,
              data: [100, 50, 75, 75, 25, 75, 50, 75, 50, 50, 75, 75],
              borderRadius: {
                topLeft: [10, 10],
                topRight: [10, 10],
                bottomLeft: [0, 0],
                bottomRight: [0, 0],
              },
            },
          ],
        },
        options: {
          plugins: {
            title: {
              display: true,
              text: 'Skills Chart',
            },
            legend: {
              display: true,
            },
          },
          scales: {
            x: {
              type: 'category',
              position: 'bottom',
            },
            y: {
              type: 'linear',
              position: 'left',
              ticks: {
                stepSize: 25,
                beginAtZero: true,
                max:100,
                callback: function (value) {
                  switch (value) {
                    case 25:
                      return 'Beginner';
                    case 50:
                      return 'Intermediate';
                    case 75:
                      return 'Advanced';
                    case 100:
                      return 'Expert';
                    default:
                      return '';
                  }
                },
              },
            },
          },
        },
      });
    },
  },
 
};
</script>

