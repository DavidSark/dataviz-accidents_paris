<script setup>
import { reactive, ref, onMounted } from 'vue';

//import d'un graphique typeLineChart
import { Line } from 'vue-chartjs'

//import des objets du graphique de la bibliothèque chartjs
//voir la documentation pour descriptif des éléments 
import {
    Chart as ChartJS, Title, Tooltip, Legend, PointElement, LineElement, LineController,
    CategoryScale, LinearScale, Filler
} from 'chart.js'

//éléments utilisés par notre graphique registration pour vue-chart
ChartJS.register(Title, Tooltip, Legend, PointElement, LineElement, LineController, CategoryScale, LinearScale, Filler)

//propriétés du graphique utilisés dans le template (props)
// on définit pour chacune son type de données et sa valeur par défaut
// on peut utiliser une grande variété de types, voire des objets

const propChart = defineProps({
    chartId: { type: String, default: 'line-chart' },
    datasetIdKey: { type: String, default: 'label' },
    width: { type: Number, default: 200 },
    height: { type: Number, default: 100 },
    cssClasses: { type: String, default: '' },
    styles: { type: Object, default: () => { } },
    plugins: { type: Object, default: () => { } },

    //données du graphe

})

//données injectée dans le graphique 
let chartData = reactive({
    labels: ['2005', '2006', '2007', '2008', '2009', '2010', '2011', '2012', '2013', '2014', '2015', '2016', '2017'],
    //valeurs des données du graphique
    //3 datasets, en un premier temps les données sont statiques (jeux de test)
    //elles seront écrasées par les donnée réelle provenant de l'api
    datasets: [
        {
            //etiquette du jeu de données à projeter
            label: "2007 est l'année la plus accidentée avec 5 399 accidents",
            //valeurs des données (statiques pour pour l'exemple)
            data: [5282, 5241, 5399, 5077, 5060, 4588, 4905, 4549, 4351, 4719, 4714, 4674, 4828],
            borderColor: 'rgba(255,0,0,0.5)',
            tension: 0.5,
            fill: true,
            backgroundColor: 'rgba(227, 227, 227,0.2)',
            pointBackgroundColor: '#fff', //couleur de fond du point
            pointBorderColor: '#ffb88c', //bordure entourant le point
            pointHoverBackgoundColor: '#ffb88c', //couleur de fond du point au passage de la souris
            pointHoverBorderColor: '#fff', //bordure entourant le point au passage de la souris 
            pointRadius: 4, //rayon du point 
            pointHoverRadius: 6, //rayon du point au passage de la souris
        },]
})

//option du graphique 
//les principaux utilisées ils en existe beaucoup d'autre 
//voir la doc
let chartOptions = reactive({

    //aspect responsive du graphique 
    responsive: true,
    scales: {
        //axe des ordonnées 
        y: {
            //valeur max des y
            suggestedMax: 6000,
            ticks: {
                font: {

                }
            }
        }
    },
    //les plugins
    plugins: {
        //titre du graphique
        title: {
            //affichage
            display: true,
            //libellé du graphique 
            text: "Nombre d'accidents totaux par année en France",
            //police de test
            font: {
                size: 16
            }
        }
    }
})





</script>


<template>
    <main>
        <Line :chart-options="chartOptions" :chart-data="chartData" :chart-id="chartId" :dataset-id-key="datasetIdKey"
            :plugins="plugins" :css-classes="cssClasses" :styles="styles" :width="width" :height="height">

        </Line>
    </main>
</template>