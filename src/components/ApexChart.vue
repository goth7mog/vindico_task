<template>
    <v-container fluid>
        <div id="chart">
            <apexchart type="bar" height="350" :options="chartOptions" :series="series"></apexchart>
        </div>
    </v-container>
</template>
  
<script>

export default {
    props: ["posts"],
    computed: {
        series() {
            const dataInPractise = this.posts.map(function (post) {
                return post.oversInPractice;
            });
            const dataInCompetition = this.posts.map(function (post) {
                return post.oversInCompetition;
            });

            return [{
                name: 'Overs in Practise',
                data: dataInPractise,
            }, {
                name: 'Overs in Competition',
                data: dataInCompetition
            }]
        },
        chartOptions() {
            const names = this.posts.map(function (post) {
                return post.bowlerName;
            });
            return {
                chart: {
                    type: 'bar',
                    height: 350,
                    stacked: true,
                },
                plotOptions: {
                    bar: {
                        horizontal: true,
                    },
                },
                stroke: {
                    width: 1,
                    colors: ['#fff']
                },
                title: {
                    text: undefined,
                },
                xaxis: {
                    categories: names,
                    labels: {
                        formatter: function (val) {
                            return val;
                        }
                    },
                    title: {
                        text: "Overs Bowled",
                        style: {
                            fontSize: '14px',
                        },
                    },

                },
                yaxis: {
                    title: {
                        text: "Team",
                        style: {
                            fontSize: '14px',
                        },
                        offsetX: 10,
                    },
                    labels: {
                        show: true,
                    },
                },
                tooltip: {
                    enabled: true,
                },
                fill: {
                    opacity: 1,
                    colors: ['#67b7dc', '#6794dc']
                },
                legend: {
                    show: false,
                },
                states: {
                    hover: {
                        filter: {
                            type: 'none'
                        }
                    }
                }
            }
        }

    },
}
</script>