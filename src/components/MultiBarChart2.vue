<script setup>
//import des éléments de vue
import { reactive } from 'vue';

//import d'un type de graphique de type barChart
import { Bar } from 'vue-chartjs'

//import des objets graphiques de la bibliotheque chartJs
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'

//élement utilisés par le graphique
ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)

//propriété du graphique utilisée dans le template
//on definit son type de donnée et sa valeur par défaut
//On peut utiliser une grande variété de types, voire des objets
const propChart = defineProps({
    chartId: { type: String, default: 'bar-chart' }, //Id du graphique
    datasetIdKey: { type: String, default: 'label' }, //Id du dataset
    width: { type: Number, default: 150 }, //largeur
    height: { type: Number, default: 60 }, //hauteur
    cssClasses: { type: String, default: '' }, //Classes css utilisées
    styles: { type: Object, default: () => { } }, //Id du graphique
    plugins: { type: Object, default: () => { } }, //Information personnalisé plugin
})

//données injectée dans le graphique
let chartData = reactive({
    //etiquette de l'axe
    labels: ['75 112', '75 111', '75 116', '75 113', '75 110'],
    //valeurs des données du graphique
    datasets: [{
        //Etiquette du jeu de donnée à projeter
        label: 'Tracé rectiligne',
        //valeurs des données
        data: [664, 637, 433, 476, 473],
        //couleurs des bars en regard des valeurs
        backgroundColor: [
            'rgba(0, 116, 255, 0.2)',
        ],
        //couleur de chaque bordure de chaque barre
        borderColor: [
            'rgb(0, 116, 255)',
        ],
        borderWidth: 1,
    },
    {

        //Etiquette du jeu de donnée à projeter
        label: 'Non référencé',
        //valeurs des données
        data: [73, 51, 63, 47, 37],
        //couleurs des bars en regard des valeurs
        backgroundColor: [
            'rgba(0, 255, 50, 0.2)',
        ],
        //couleur de chaque bordure de chaque barre
        borderColor: [
            'rgba(0, 255, 50)',
        ],
        borderWidth: 1,
    },
    {

        //Etiquette du jeu de donnée à projeter
        label: 'En courbe à gauche',
        //valeurs des données
        data: [38, 21, 38, 11, 8],
        //couleurs des bars en regard des valeurs
        backgroundColor: [

            'rgba(255, 97, 0, 0.2)',

        ],
        //couleur de chaque bordure de chaque barre
        borderColor: [

            'rgb(255, 97, 0)',

        ],
        borderWidth: 1,
    },
    {

        //Etiquette du jeu de donnée à projeter
        label: 'En courbe à droite',
        //valeurs des données
        data: [34, 9, 69, 6, 6],
        //couleurs des bars en regard des valeurs
        backgroundColor: [

            'rgba(255, 0, 251, 0.2)',

        ],
        //couleur de chaque bordure de chaque barre
        borderColor: [
            'rgb(255, 0, 251)',
        ],
        borderWidth: 1,
    },
    {
        //Etiquette du jeu de donnée à projeter
        label: 'En "S"',
        //valeurs des données
        data: [1, 0, 0, 0, 0],
        //couleurs des bars en regard des valeurs
        backgroundColor: [
            'rgba(106, 111, 125, 0.2)',
        ],
        //couleur de chaque bordure de chaque barre
        borderColor: [
            'rgb(106, 111, 125)',
        ],
        borderWidth: 1,
    }]
})

//options du graphique
//les principales utilisées, ils en existe d'autres
//voir documentation
let chartOptions = reactive({
    //Aspect responsive du graphique
    responsive: true,
    //maintien du ratio
    maintainAspectRation: false,

    //Types de projection utilisée
    //x: verticale (par defaut)
    //y: horizontale
    indexAxis: "x",

    //Echelle du graphique
    scales: {
        //axe des ordonnées 
        y: {
            //valeur max des y
            suggestedMax: 700,
            ticks: {
                font: {
                    size: 16
                },
            }
        },
        //axe des abscisses
        x: {
            ticks: {
                font: {
                    size: 16
                }
            }
        }
    },

    //Plugins 
    plugins: {
        //légende des données
        legend: {
            labels: {
                color: 'black',
                font: {
                    size: 16
                }
            }
        },
        title: {
            //affiche titre
            display: true,
            //libellé du graphique 
            text: "Tracé du plan de la route des 5 communes les plus accidentées de 2005 à 2017",
            //couleur du text
            color: "black",
            font: {
                size: 16
            }
        }
    },
})
</script>

<template>
    <Bar :chart-options="chartOptions" :chart-data="chartData" :chart-id="chartId" :dataset_id_key="datasetIdKey"
        :plugins="plugins" :css-classes="cssClasses" :styles="styles" :width="width" :height="height" />
</template>

<style scoped>

</style>