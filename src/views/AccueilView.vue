<script setup lang="ts">
import BarChart from '../components/BarChart.vue';
import HorizontalBarChart from '../components/HorizontalBarChart.vue';
import MiniBarChart2005 from '../components/MiniBarChart2005.vue';
import MiniBarChart2010 from '../components/MiniBarChart2010.vue';
import MiniBarChart2017 from '../components/MiniBarChart2017.vue';
import MultiBarChart from '../components/MultiBarChart.vue';
import MultiBarChart2 from '../components/MultiBarChart2.vue';
import PieChart from '../components/PieChart.vue';
import RadarChart from '../components/RadarChart.vue';
import ScatterChart from '../components/StackedChart.vue';
import LineChart from '../components/LineChart.vue';
import MultiLineChart from '../components/MultiLineChart.vue';
import DoubleBarChart from '../components/DoubleBarChart.vue';

</script>

<template>
  <div>
    <div class="bg-bg">
      <div class="flex mx-auto pt-20">
        <div class="flex justify-center flex-col w-1/2 px-8 py-16">
          <h1 class="font-Roboto text-5xl leading-tight font-bold">ENQUETE. Accidents
            de vélo : Paris et ses
            accidents de vélos
            particuliérement
            dangereux</h1>

          <div class="pt-5">
            <p class="font-Roboto ">Ecrit et publier par David Sarkissian</p>
            <p class="font-Roboto">Mise en place le 02/11/2022 à 9h00</p>
          </div>
        </div>

        <div class="flex justidy-center items-center flex-col w-1/2 px-8 py-16">
          <figure class="m-0">
            <img class="max-w-full w-full" src="../assets/img/img_accueil.webp" alt="image de vélo" />
            <figcaption class="font-Roboto">Un accident en agglomération, dans une rue à Paris.</figcaption>
          </figure>
        </div>
      </div>
    </div>

    <div class="flex justify-center flex-col px-96 mt-24">

      <h2 class="font-Roboto text-4xl leading-tight font-semibold">Le vélo a toujours été un moyen de transport
        utilisé pour se
        déplacer
        efficacement
        et rapidement par
        énormément de français.
        Que ce soit pour son bien-être, l'environnement ou encore le côté pratique, la thématique du vélo possède
        également son lot de malheur.</h2>

      <div class="text-3xl leading-normal mt-10">

        <p>
          Il ne faut pas oublier que même à vélo le pire peut arriver. Les cyclistes sont également
          des usagers de la route et ne font pas exception au Code de la route. Trop souvent
          ce détail est négligé et un accident est vite arrivé.
        </p>

        <LineChart class="mt-10"></LineChart>
        <p class="text-base">Source : <a
            href="https://docs.google.com/spreadsheets/d/1mxwuEVeyPJyB-vkCiQV-ip5iwGLis98xnupgs4uPFTU/edit#gid=320478493"
            target="_blank">accidents
            vélos 2005-2017</a>
        </p>

        <p class="mt-10">Et pour cause, on recense un total de 63 387 accidents dans toute la France sur une période
          allant de <span class="font-bold">2005 à 2017</span> avec un pic d'accidents atteignant 5 399 pour l'année de
          2007. Mais ce qui est
          étonnant avec ces accidents, c'est que
          le plus grand
          nombre de
          ces accidents se produisent dans la Capitale : Paris.
        </p>

      </div>


      <BarChart class="mt-10"></BarChart>
      <p>Source : <a
          href="https://docs.google.com/spreadsheets/d/1mxwuEVeyPJyB-vkCiQV-ip5iwGLis98xnupgs4uPFTU/edit#gid=320478493"
          target="_blank">accidents
          vélos 2005-2017</a>
      </p>

      <div class="text-3xl leading-normal mt-10">
        <p>On se rend très vite compte du nombre d'accidents provoqués à Paris durant cette période de
          2005 à 2017.<br /> Pour le même nombre d'années (12 ans) le département du Rhône (69) recense 2 461
          accidents tandis que le département de la Gironde (33) recense 2 338 accidents impliquant des vélos.
          On est très clairement loin des 9 789 accidents du département de Paris.

        </p>
        <div class="bg-bg mt-10">
          <div class="flex mx-auto ">
            <div class=" flex justify-center flex-col w-1/2 px-8">

              <MiniBarChart2005 />
              <MiniBarChart2010 />
              <MiniBarChart2017 />

            </div>

            <div class=" flex justidy-center items-center flex-col w-6/12 px-8 big:justify-around">
              <p class="py-10 leading-relaxed font-Roboto text-lg big:text-2xl ">Ces trois graphiques
                ci-contre montrent
                les trois
                départements les plus
                accidentés à une
                année
                donnée.
                Dès lors il est possible de distinguer l'impact qu'à pu avoir l'évolution de
                l'utilisation du vélo.
                Dès 2005 il y a effectivement énormément d'accidents dans le département du 75.
                Sur toute l'année de 2005 on compte 516 accidents.
                Et cela ne va pas en s'arrangeant car les années suivantes, Paris reste le département où l'on recense
                le plus d'accidents.
                En 2010 le nombre d'accidents passe à 620 et en 2017, ce nombre passe à 782.
                On se rend donc vite compte du nombre d'accidents de vélo provoqués dans la Capitale.
              </p>
            </div>
          </div>

        </div>
      </div>

      <div class="mt-10">
        <h2 class="text-4xl font-semibold">
          Des communes trop accidentées
        </h2>

        <p class="mt-10 text-3xl leading-normal ">
          Mais alors quels sont les arrondissements de Paris les plus impactés par ces accidents ?
        </p>
      </div>

      <HorizontalBarChart class="mt-10"></HorizontalBarChart>
      <p>Source : <a
          href="https://docs.google.com/spreadsheets/d/1mxwuEVeyPJyB-vkCiQV-ip5iwGLis98xnupgs4uPFTU/edit#gid=320478493"
          target="_blank">accidents
          vélos 2005-2017</a>
      </p>

      <div class=" mt-10 text-4xl font-semibold  flex flex-col items-end">
        <div class="border-l-4 border-black">
          <p class="pl-4  ">"J'ai pensé que j'allais mourir "</p>
          <p class="pl-4 text-base">Le <a class="bg-slate-200"
              href="https://www.leparisien.fr/faits-divers/jai-pense-que-jallais-mourir-le-recit-glacant-des-temoins-du-grave-accident-de-la-route-dans-le-xiiie-a-paris-12-12-2021-JXEETCLLE5H7RIDVVDOY2BZCZU.php">récit</a>
            d'un cycliste percuté par une voiture dans le 13éme.</p>
        </div>
      </div>

      <div>
        <p class="mt-10 text-3xl leading-normal"> Sur ces 12 ans, les cinq communes ayant le plus d'accidents sont le
          12eme,11eme, 16eme, 13eme et 10eme arrondissements.
        </p>
        <p class="mt-10 text-3xl leading-normal">
          Mais les données des accidents révèlent un fait pour le moins très surprenant.
          On pourrait penser que les accidents ont lieu à des moments de la journée, où les conditions
          environnementales sont les pires pour sortir à vélo.
        </p>
      </div>

      <MultiLineChart class="mt-10"></MultiLineChart>

      <p class="text-base">Source : <a
          href="https://docs.google.com/spreadsheets/d/1mxwuEVeyPJyB-vkCiQV-ip5iwGLis98xnupgs4uPFTU/edit#gid=320478493"
          target="_blank">accidents
          vélos 2005-2017</a>
      </p>
      <div class="mt-10">
        <p class="text-3xl leading-normal">
          Mais l'ensemble des accidents ont lieu dans un environnement où les conditions
          de visibilité sont optimales puisqu'on se retrouve à avoir énormément plus d'accidents en plein jour que de
          nuit, ce qui est pour le moins surprenant.
        </p>

        <p class="mt-10 text-3xl leading-normal">Lorsque l'on parle de condition environnementale, la luminosité est un
          point
          important, mais il ne faut pas
          non plus négligé les conditions atmosphériques car celles-ci jouent un rôle qu'il ne faut pas sous-estimé.
          Et pour cause, on pourrait également penser que les accidents ont lieu à des moments où la pluie, le vent ou
          même la neige sont déchainés.
        </p>
        <PieChart class="mt-10"></PieChart>
        <p class="text-base">Source : <a
            href="https://docs.google.com/spreadsheets/d/1mxwuEVeyPJyB-vkCiQV-ip5iwGLis98xnupgs4uPFTU/edit#gid=320478493"
            target="_blank">accidents
            vélos 2005-2017</a>
        </p>
        <p class="mt-10 text-3xl leading-normal">Là encore, sur tous les accidents enregistrés en France, plus de 57 000
          de
          ces
          accidents ont lieu lors de
          conditions
          météorologiques normales.
          Mais alors si ces conditions atmosphériques sont normales, est-ce le tracé de la route qui est impraticable?
        </p>
        <MultiBarChart2 class="mt-10"></MultiBarChart2>
        <p class="text-base">Source : <a
            href="https://docs.google.com/spreadsheets/d/1mxwuEVeyPJyB-vkCiQV-ip5iwGLis98xnupgs4uPFTU/edit#gid=320478493"
            target="_blank">accidents
            vélos 2005-2017</a>
        </p>
        <p class="mt-10 text-3xl leading-normal">
          Tout aussi surprenant que les conditions de visibilité et météorologique, les accidents à vélo surviennent le
          plus
          sur des routes à tracé rectiligne, c'est-à-dire en ligne droite.
          Les cyclistes ont donc du mal à prendre en compte leur environnement même lorsqu'il s'agit
          de route simple.
        </p>
        <p class="mt-10 text-3xl leading-normal">
          Une répartition des sexes pourrait nous en apprendre davantage sur qui sont
          sont ses usagers qui, sur un tracé rectiligne, ont le plus d'accidents?
        </p>

        <DoubleBarChart class="mt-10"></DoubleBarChart>
        <p class="text-base">Source : <a
            href="https://docs.google.com/spreadsheets/d/1mxwuEVeyPJyB-vkCiQV-ip5iwGLis98xnupgs4uPFTU/edit#gid=320478493"
            target="_blank">accidents
            vélos 2005-2017</a>
        </p>
        <p class="mt-10 text-3xl leading-normal">
          C'est donc en majorité les hommes qui se retrouvent à chuter le plus souvent, bien que les femmes aient
          elles aussi une présence dans cette répartition des sexes.
          Cela dit, les hommes ont plus de mal à se diriger sur un plan rectiligne que les femmes.
        </p>

      </div>
      <div class=" mt-10 text-3xl leading-normal font-Roboto">
        <h2 class="text-4xl font-semibold">
          Accidents sans trop de gravités?
        </h2>
        <p class="mt-10">
          Qu'il y ait des accidents est une chose, mais quand est il de la gravité de ceux-ci ?
        </p>
        <ScatterChart class="mt-10"></ScatterChart>
        <p class="text-base">Source : <a
            href="https://docs.google.com/spreadsheets/d/1mxwuEVeyPJyB-vkCiQV-ip5iwGLis98xnupgs4uPFTU/edit#gid=320478493"
            target="_blank">accidents
            vélos 2005-2017</a>
        </p>
        <p class="mt-10">
          Inéluctablement, ces grands nombres d'accidents dans les communes de Paris font des morts.
          En 12 ans, pour les cinq communes les plus accidentées on recense 15 décès au total.
          Cela pourrait paraître peu, mais une vie est une vie et le but est de réduire considérablement
          le nombre de décès.
          Dans son ensemble ces accidents ne provoquent que de légère blessure, sinon des cyclistes indemnes
          ou hospitalisés.
        </p>
      </div>

      <div class="mt-10 text-3xl leading-normal font-Roboto">
        <h2 class="text-4xl font-semibold">
          Lieux et infrastructures
        </h2>
        <p class="mt-10">
          Ces accidents n'ont pas lieu n'importe ou. Trop de cyclistes sont victimes d'accidents
          sur la chaussée.
        </p>
        <MultiBarChart class="mt-10"></MultiBarChart>
        <p class="text-base">Source : <a
            href="https://docs.google.com/spreadsheets/d/1mxwuEVeyPJyB-vkCiQV-ip5iwGLis98xnupgs4uPFTU/edit#gid=320478493"
            target="_blank">accidents
            vélos 2005-2017</a>
        </p>
        <p class="mt-10">
          On le constate clairement, les accidents sur la route sont les plus nombreux et ça pour les cinq
          communes les plus accidentées de Paris.
          Cela dit, en comparaison, on se rend compte que les accidents sur piste cyclable et trottoir sont
          moins légion.

        </p>
        <p class="mt-10 mb-20 ">
          Nullifier totalement les accidents n'est malheureusement pas possible.
          L'erreur est humaine et malgré toute la sensibilisation du monde, les usagers auront toujours
          des accidents car il est compliqué de rester tout le temps concentré sur tout ce qui se passe
          sur la route.
          Cela dit, l'étude des graphiques a pu démontrer que les accidents ont souvent lieu sur la chaussée
          et ainsi l'aménagement de plus de piste cyclable pourraient grandement diminuer les accidents
          impliquant des vélos car ils sont trop souvent obligés de suivre les mêmes routes que les
          automobilistes et cela a parfois trop de conséquence pour eux, comme pour les autres usagers de la
          route.
        </p>
      </div>




      <!-- 
      <div class=" flex justify-center flex-col w-1/2 px-8>
        <div class="w-6/12">
          <MiniBarChart2005 />
          <MiniBarChart2010 />
          <MiniBarChart2017 />
        </div>
        <div class="">
          <p></p>
        </div>
      </div> -->




    </div>

  </div>
</template>

