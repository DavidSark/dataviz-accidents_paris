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
    labels: ['Tracé rectiligne', 'Courbe à gauche', 'Courbe à droite', 'Route en "S"', 'Non référencé'],
    //valeurs des données du graphique
    datasets: [{

        //Etiquette du jeu de donnée à projeter
        label: 'Hommes',
        //valeurs des données
        data: [38353, 3343, 2767, 529, 4604],
        //couleurs des bars en regard des valeurs
        backgroundColor: [

            'rgba(255, 159, 64, 0.2)',

        ],
        //couleur de chaque bordure de chaque barre
        borderColor: [

            'rgb(255, 159, 64)',

        ],
        borderWidth: 1,
    },
    {

        //Etiquette du jeu de donnée à projeter
        label: 'Femmes',
        //valeurs des données
        data: [13171, 984, 643, 93, 1494],
        //couleurs des bars en regard des valeurs
        backgroundColor: [
            'rgba(255, 99, 132, 0.2)',

        ],
        //couleur de chaque bordure de chaque barre
        borderColor: [
            'rgb(255, 99, 132)',

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

            ticks: {
                font: {
                    size: 16
                }
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
            text: "Répartition des sexes des accidents totaux sur les tracés de route pour la période 2005-2017",
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