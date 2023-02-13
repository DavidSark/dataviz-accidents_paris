
<script setup>
import { reactive, ref, onMounted } from 'vue';
import { Doughnut } from 'vue-chartjs'
import { Chart as ChartJs, Title, Tooltip, Legend, ArcElement, CategoryScale, Chart } from 'chart.js'

Chart.register(Title, Tooltip, Legend, ArcElement, CategoryScale)

const propChart = defineProps({
    chartId: { type: String, default: 'doughnut-chart' },
    datasetIdKey: { type: String, default: 'label' },
    width: { type: Number, default: 500 },
    height: { type: Number, default: 500 },
    cssClasses: { type: String, default: '' },
    styles: { type: String, default: () => { } },
    plugins: { type: String, default: () => { } },
})

const chartData = reactive({
    labels: [],
    datasets: [
        {
            data: [],
            backgroundColor: [],
            borderColor: [],
            borderWidth: 1
        }
    ]
})


const chartOptions = reactive({

    responsive: true,
    maintainAspectRatio: false
})

let liste = ref();
let listeAtmo = new Set()

onMounted(async () => {
    fetch('https://accidentvelo.jmfino.fr/json.php')
        .then(response => response.json())
        .then(response => {
            liste = response
            // console.log(liste);
            liste.forEach(accident => {
                listeAtmo.add(accident[10])
            })
            listeAtmo.delete()

            // console.log(listeInter)
            chartData.labels = Array.from(listeAtmo)
            console.log(chartData.labels)
            // chartData.labels.sort()
            let cpt = []
            chartData.labels.forEach((inter) => {
                let nb = 0
                liste.forEach((acc) => {
                    if (inter == acc[10])
                        nb++
                })
                cpt.push(nb)
            })
            chartData.datasets[0].data = cpt
            console.log(cpt);

            let bgColor = [];
            let bdColor = [];
            cpt.forEach(function (val) {
                let c1 = couleur(0, 255)
                let c2 = couleur(0, 255)
                let c3 = couleur(0, 255)
                let tr = 0.5
                let color = 'rgba(' + [c1, c2, c3, tr].join(',') + ")"
                bgColor.push(color)
                let border = 'rgba(' + [c1, c2, c3, tr].join(',') + ")"
                bdColor.push(color)
            })
            chartData.datasets[0].backgroundColor = bgColor;
            chartData.datasets[0].borderColor = bdColor;

        })
        .catch(error => console.log('erreur Ajax'))


})

const couleur = (min, max) => {
    return Math.floor(Math.random() * (max - min));
}
</script>
        
<template>
    <Doughnut :chart-options="chartOptions" :chart-data="chartData" :chart-id="chartId" :dataset-id-key="datasetIdKey"
        :plugins="plugins" :css-classes="cssClasses" :styles="styles" :width="width" :height="height" />
</template>


<!-- <script setup>
import { reactive, ref, onMounted } from 'vue';
import { Doughnut } from 'vue-chartjs'
import { Chart as ChartJs, Title, Tooltip, Legend, ArcElement, CategoryScale, Chart } from 'chart.js'

Chart.register(Title, Tooltip, Legend, ArcElement, CategoryScale)

const propChart = defineProps({
    chartId: { type: String, default: 'doughnut-chart' },
    datasetIdKey: { type: String, default: 'label' },
    width: { type: Number, default: 500 },
    height: { type: Number, default: 500 },
    cssClasses: { type: String, default: '' },
    styles: { type: String, default: () => { } },
    plugins: { type: String, default: () => { } },
})

const chartData = reactive({
    labels: ['2005', '2006', '2007', '2008', '2009', '2010', '2011', '2012', '2013', '2014', '2015', '2016', '2017'],
    datasets: [{
        //Etiquette du jeu de donnée à projeter
        label: 'Département le plus accidenté',
        //valeurs des données
        data: [5282, 5241, 5399, 5077, 5060, 4588, 4905, 4549, 4351, 4719, 4714, 4674, 4828],
        //couleurs des bars en regard des valeurs
        backgroundColor: [
            'rgba(255, 99, 132, 0.2)',
            'rgba( 118, 160, 26 , 0.2)',
            'rgba(255, 159, 64, 0.2)',

            'rgba(255, 205, 86, 0.2)',
            'rgba(75, 192, 192, 0.2)',
            'rgba(117, 225, 223 , 0.2)',
            'rgba(54, 164, 235, 0.2)',
            'rgba(225, 148, 117 , 0.2)',
            'rgba(225, 117, 151 , 0.2)',
            'rgba(106, 111, 125, 0.2)',

            'rgba(197, 225, 117, 0.2)',

            'rgba(117, 225, 187, 0.2)',
            'rgba(212, 117, 225 , 0.2)',



        ],
        //couleur de chaque bordure de chaque barre
        borderColor: [
            'rgba(255, 99, 132, 0.2)',
            'rgba( 118, 160, 26 , 0.2)',
            'rgba(255, 159, 64, 0.2)',

            'rgba(255, 205, 86, 0.2)',
            'rgba(75, 192, 192, 0.2)',
            'rgba(117, 225, 223 , 0.2)',
            'rgba(54, 164, 235, 0.2)',
            'rgba(225, 148, 117 , 0.2)',
            'rgba(225, 117, 151 , 0.2)',
            'rgba(106, 111, 125, 0.2)',

            'rgba(197, 225, 117, 0.2)',

            'rgba(117, 225, 187, 0.2)',
            'rgba(212, 117, 225 , 0.2)',
        ],
        borderWidth: 1,
    }]
})


const chartOptions = reactive({
    responsive: true,
    maintainAspectRatio: false
})



</script>
        
<template>
    <Doughnut :chart-options="chartOptions" :chart-data="chartData" :chart-id="chartId" :dataset-id-key="datasetIdKey"
        :plugins="plugins" :css-classes="cssClasses" :styles="styles" :width="width" :height="height" />
</template>``` -->