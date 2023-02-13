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
    labels: ['75 112', '75 111', '75 116', '75 113', '75 110'],
    //valeurs des données du graphique
    //3 datasets, en un premier temps les données sont statiques (jeux de test)
    //elles seront écrasées par les donnée réelle provenant de l'api
    datasets: [
        {
            //etiquette du jeu de données à projeter
            label: 'Plein jour',
            //valeurs des données (statiques pour pour l'exemple)
            data: [638, 519, 494, 391, 370],
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
        },
        {
            //etiquette du jeu de données à projeter
            label: 'Nuit avec éclairage',
            //valeurs des données (statiques pour pour l'exemple)
            data: [127, 156, 74, 125, 127],
            borderColor: 'rgba(240, 185, 77 ,0.5)',
            tension: 0.5,
            fill: true,
            backgroundColor: 'rgba(227, 227, 227,0.2)',
            pointBackgroundColor: '#fff', //couleur de fond du point
            pointBorderColor: '#ffb88c', //bordure entourant le point
            pointHoverBackgoundColor: '#ffb88c', //couleur de fond du point au passage de la souris
            pointHoverBorderColor: '#fff', //bordure entourant le point au passage de la souris 
            pointRadius: 4, //rayon du point 
            pointHoverRadius: 6, //rayon du point au passage de la souris
        },
        {
            //etiquette du jeu de données à projeter
            label: 'Nuit sans éclairage',
            //valeurs des données (statiques pour pour l'exemple)
            data: [11, 13, 4, 6, 2],
            borderColor: 'rgba(0,0,255,0.5)',
            tension: 0.5,
            fill: true,
            backgroundColor: 'rgba(227, 227, 227,0.2)',
            pointBackgroundColor: '#fff', //couleur de fond du point
            pointBorderColor: '#ffb88c', //bordure entourant le point
            pointHoverBackgoundColor: '#ffb88c', //couleur de fond du point au passage de la souris
            pointHoverBorderColor: '#fff', //bordure entourant le point au passage de la souris 
            pointRadius: 4, //rayon du point 
            pointHoverRadius: 6, //rayon du point au passage de la souris
        },

        {
            //etiquette du jeu de données à projeter
            label: 'Crépuscule',
            //valeurs des données (statiques pour pour l'exemple)
            data: [34, 30, 32, 18, 25],
            borderColor: 'rgba(134, 240, 77,0.5)',
            tension: 0.5,
            fill: true,
            backgroundColor: 'rgba(227, 227, 227,0.2)',
            pointBackgroundColor: '#fff', //couleur de fond du point
            pointBorderColor: '#ffb88c', //bordure entourant le point
            pointHoverBackgoundColor: '#ffb88c', //couleur de fond du point au passage de la souris
            pointHoverBorderColor: '#fff', //bordure entourant le point au passage de la souris 
            pointRadius: 4, //rayon du point 
            pointHoverRadius: 6, //rayon du point au passage de la souris
        },
    ]
})

//option du graphique 
//les principaux utilisées ils en existe beaucoup d'autre 
//voir la doc
let chartOptions = reactive({
    //aspect responsive du graphique 
    responsive: true,
    //les plugins
    plugins: {
        //titre du graphique
        title: {
            //affichage
            display: true,
            //libellé du graphique 
            text: 'Luminosité des accidents ayant eu lieux dans les 5 communes les plus accidentées de 2005 à 2017',
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