# Projet SIG -- Cartographie thématique avec QGIS

## Présentation

Ce dépôt présente un projet de cartographie réalisé en duo avec **QGIS** dans
le cadre d'un travail universitaire. Il s'appuie sur des couches
géographiques de référence pour construire une carte thématique à
plusieurs niveaux d'échelle.

Le projet porte notamment sur : 
- la représentation de données de
population à l'échelle communale ; 
- la catégorisation de l'occupation
du sol ; 
- la représentation d'éléments administratifs, routiers et
hydrographiques ; 
- l'organisation de couches vectorielles et raster
dans un même projet cartographique ; 
- la définition de règles de
symbologie et d'affichage adaptées à l'échelle.

> **Important -- données non incluses :** les jeux de données utilisés pour ce travail étaient fournis dans l'environnement universitaire et ne sont donc pas redistribué dans ce dépot.  Le projet QGIS est conservé à titre de démonstration de la onfiguration et du travail cartographique réalisés, mais il ne peut pas être ouvert intégralement sans récupérer les données sources et rétablir les chemins des couches.

## Contenu du dépôt
  `projet.qgz`                        Projet QGIS principal, contenant
                                      les couches référencées et leurs
                                      paramètres de représentation.

  `raster.vrt`                        Description d'un raster virtuel
                                      assemblant des dalles raster
                                      externes. Il ne contient pas les
                                      pixels des données sources.

Le projet QGIS contient 13 couches configurées :

-   `AERODROME`
-   `CHEF_LIEU`
-   `COMMUNE copie`
-   `COMMUNE`
-   `COTE_FRONTIERE`
-   `DEPARTEMENT`
-   `EPCI`
-   `NOEUD_COMMUNE`
-   `Virtuel` (raster)
-   `REGION`
-   `TRONCON_HYDROGRAPHIQUE`
-   `TRONCON_ROUTE`
-   `ZONE_OCCUPATION_SOL`

## Travail cartographique réalisé

### 1. Organisation des données géographiques

Le projet regroupe des couches vectorielles relatives à différents
thèmes :

-   **Découpage administratif :** communes, départements, régions et
    EPCI ;
-   **Réseau routier :** tronçons de route et nœuds communaux ;
-   **Hydrographie :** tronçons hydrographiques ;
-   **Habillage et occupation du sol :** limites côtières/frontières et
    zones d'occupation du sol ;
-   **Autres objets :** aérodromes et chefs-lieux.

Les sources vectorielles référencées dans le projet sont principalement
des fichiers Shapefile (`.shp`).

Le système de coordonnées du projet est **RGF93 / Lambert-93
(EPSG:2154)**, adapté à la cartographie du territoire français
métropolitain.

### 2. Cartographie thématique de la population

La couche `COMMUNE copie` utilise une **symbologie graduée** fondée sur
le champ `POPULATION`.

Les valeurs sont réparties en huit intervalles configurés dans le projet
:

-   0 à 100 ;
-   100 à 1 000 ;
-   1 000 à 5 000 ;
-   5 000 à 20 000 ;
-   20 000 à 50 000 ;
-   50 000 à 100 000 ;
-   100 000 à 250 000 ;
-   250 000 à 2 500 000.

Cette représentation permet de comparer visuellement les niveaux de
population entre communes.

### 3. Occupation du sol

La couche `ZONE_OCCUPATION_SOL` utilise une **symbologie catégorisée** à
partir du champ `NATURE`.

Les catégories configurées comprennent : - Forêt ; - Bâti ; - Eau.

### 4. Représentation selon l'échelle

Plusieurs couches utilisent des règles de rendu conditionnées par des
attributs et/ou des dénominateurs d'échelle.

Exemples présents dans la configuration : - les chefs-lieux sont
différenciés selon leur statut (capitale d'État, préfecture de région,
préfecture, sous-préfecture et commune simple) ; - les tronçons
hydrographiques sont distingués selon leur classe de largeur ; - les
tronçons routiers sont différenciés selon leur classe administrative
(autoroute, nationale, départementale, etc.).

Ces règles permettent d'adapter le niveau de détail affiché au niveau de
zoom et d'éviter de représenter tous les objets de la même manière à
toutes les échelles.

## Données et limites de reproduction

Les données sources ne sont **pas présentes dans ce dépôt**. Le fichier
`.qgz` enregistre principalement la configuration du projet QGIS et les
références vers les données ; il n'intègre pas automatiquement les
fichiers Shapefile ou les rasters externes.

Les chemins enregistrés dans le projet sont relatifs à une arborescence
de données utilisée à l'université. Le fichier `raster.vrt` référence
également des dalles JPEG 2000 (`.jp2`) stockées dans un répertoire
externe (`C:/Data/Data/SCAN1000/...`). Le VRT décrit une mosaïque raster
de **14 000 × 12 000 pixels**, en trois bandes, mais ne contient pas les
dalles elles-mêmes.

En conséquence : - certaines couches apparaîtront comme indisponibles à
l'ouverture du projet ; - le raster virtuel ne pourra pas être affiché
sans les fichiers `.jp2` référencés ; - les rendus, classes, règles et
paramètres configurés restent consultables dans le projet lorsque QGIS
permet d'accéder à sa configuration, mais l'affichage cartographique
complet n'est pas garanti.

Aucune donnée universitaire ou donnée géographique sous licence n'est
incluse ou redistribuée ici.

## Ouvrir le projet

1.  Installer [QGIS](https://qgis.org/).
2.  Cloner ou télécharger ce dépôt.
3.  Ouvrir `projet.qgz` dans QGIS.
4.  En l'absence des données sources, QGIS signalera des couches
    manquantes.

Pour retrouver un affichage complet, il faut disposer légalement des
jeux de données d'origine, puis rétablir les chemins vers les fichiers
correspondants dans les propriétés des couches. Pour le raster, il faut
également rendre accessibles les dalles `.jp2` référencées dans
`raster.vrt`.

## Compétences mobilisées

-   QGIS et organisation de projets SIG ;
-   manipulation de données géographiques vectorielles et raster ;
-   système de coordonnées RGF93 / Lambert-93 ;
-   cartographie thématique et symbologie graduée ;
-   catégorisation de données ;
-   étiquetage et règles de représentation ;
-   gestion de l'affichage selon l'échelle.

## Contexte

Projet universitaire réalisé en duo avec des données mises à disposition dans
le cadre des enseignements. Les fichiers de données d'origine n'étant
plus disponibles de mon côté, ce dépôt documente le travail et conserve
le projet QGIS, sans prétendre fournir une démonstration cartographique
autonome ou reproductible en l'état.
