<!-- <script setup>
import { reactive, ref, onMounted } from 'vue';

import { Radar } from 'vue-chartjs';

import {
    Chart as ChartJS, Title, Tooltip, Legend, PointElement, LineElement,
    RadialLinearScale, Filler
} from 'chart.js'

//éléments utilisées par notre graphique registration pour vue-chart
ChartJS.register(Title, Tooltip, Legend, PointElement, LineElement, RadialLinearScale, Filler)

const propChart = defineProps({
    chartId: { type: String, default: 'radar-chart' }, //Id du graphique
    datasetIdKey: { type: String, default: 'label' }, //Id du dataset
    width: { type: Number, default: 200 }, //largeur
    height: { type: Number, default: 100 }, //hauteur
    cssClasses: { type: String, default: '' }, //Classes css utilisées
    styles: { type: Object, default: () => { } }, //Id du graphique
    plugins: { type: Object, default: () => { } }, //Information personnalisé plugin
})


let chartData = reactive({
    labels: ['Janvier', 'Février', 'Mars ', 'Avril', 'Mai'],

    datasets: [
        {
            label: 'Femmes',
            data: [40, 20, 30, 10, 32],
            borderColor: 'rgba(255,0,0,0.5)',
            fill: true
        },
        {
            label: 'Hommes',
            data: [40, 20, 30, 10, 32],
            borderColor: 'rgba(0,0,255,0.5)',
            fill: true
        }
    ]

});

let chartOptions = reactive({
    responsive: true,
    scales: {
        r: {
            angleLines: {
                display: true,
                text: 'accidents vélos',
                font: {
                    size: 16
                }
            }
        }
    }
})


let theme = [
    { id: 1, lib: 'par année' },
    { id: 2, lib: 'par département' },
]

let themeSelect = ref()
themeSelect.value = 1

let total = ref()
total.value = 0

let liste = ref()

onMounted(async () => {
    let request = "https://accidentvelo.jmfino.fr/json.php"
    await fetch(request).then(response => response.json()).then(response => {
        liste.value = response
        console.log("liste", liste)
        console.log("nb de lignes", liste.value.length)

        let anneeMax = 0
        let anneeMin = 000
        liste.value.forEach((el) => {
            let dt = el[1].split("-")
            if (dt[0] < anneeMin) {
                anneeMin = dt[0]
            }
            if (dt[0] > anneeMax) {
                anneeMax = dt[0]
            }
        })
        chartOptions.plugins.title.text = chartOptions.plugin.title.text + ' de ' + anneeMin + ' à ' + anneeMax
    })
        .catch(error => console.log('erreur Ajax', error))
})
</script>

<template>
    <div class="container-fluid bg-light">
        <h1 class="text-dark">Graphique Radar</h1>
        <form>
            <div class="form-row">
                <div class="col-7">
                    <select class="form-control" v-model="themeSelect" @change="selection(themeSelect)">
                        <option v-for="th in theme" :key="th.id" :value="th.id">
                            {{ th.id }}-{{ th.lib }}
                        </option>
                    </select>
                </div>
                <div class="col-3">
                    <input class="form-control" type="text" value="total" readonly />
                </div>
                <div class="col-3">
                    <input class="form-control" type="text" :value="total" readonly />
                </div>
            </div>
        </form>
        <div v-if="loading">
            <div class="container">
                <Radar :chart-options="chartOptions" :chart-data="chartData" :chart-id="chartId"
                    :dataset-id-key="datasetIdKey" :plugins="plugins" :css-classes="cssClasses" :styles="styles"
                    :width="width" :height="height">

                </Radar>

            </div>
        </div>
        <div v-else>

        </div>
    </div>
</template> -->