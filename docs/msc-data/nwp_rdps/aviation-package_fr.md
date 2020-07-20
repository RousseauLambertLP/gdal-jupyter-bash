[In English](aviation-package_en.md)

![ECCC logo](../../img_eccc-logo.png)

[TdM](../../readme_fr.md) > [Données du SMC](../readme_fr.md) > Prévisions pour l'aviation en 4 panneaux


# Prévisions pour l'aviation (4 panneaux)

Prévisions du modèle GEM, en configuration régionale, valides pour 6, 12, 18 et 24 heures (à 0000 et 1200). Chaque prévision est présentée sous forme de 4 panneaux, illustrés ci-dessous.

| Givrage & Niveau de congélation  |  Hauteur de la tropopause & Turbulence à haute altitude|
|--------------------------------|-------------------------------------------------------|
| Tension en surface  |  Turbulence à moyenne altitude |

* La couverture géographique pour l'ensemble des panneaux est la suivante : L'Amérique du Nord et les régions de l'Arctique, l'Atlantique Nord, le nord de l'Europe et de l'Asie et le Pacifique Nord.
* Les identificateurs de transmission sont les suivants : CMC776, CMC777, CMC778, CMC779, CMC780, CMC781, CMC782, CMC783.

__Échantillon de carte (4 panneaux)__

![echantillon de carte](http://collaboration.cmc.ec.gc.ca/cmc/cmos/public_doc/msc-data/nwp_rdps/samples_products/difax_reg_prog_aviation-package.gif)

## Givrage et Niveau de congélation (panneau supérieur gauche)

### Champs

* Niveau de congélation
    * Représentation : Lignes solides représentant la hauteur du niveau de congélation au-dessus du niveau moyen au niveau de la mer; les intervalles sont de 2 500 pi; les unités sont en centaines de pi.
* Eau surfondue (potentiel de givrage)
    * Représentation : Des lignes tiretées entourent les régions où le modèle prévoit la présence d'eau surfondue; ces régions sont indiquées par des pointillés pâles.

### Pointage

Dans les régions pointillées, la base et le sommet de la couche d'eau surfondue sont pointés en milliers de pieds au-dessus du niveau moyen au niveau de la mer, à des points de grille sélectionnés; la donnée du bas indique la base et la donnée du haut indique le sommet.
 

## Hauteur de la tropopause et Turbulence à haute altitude (panneau supérieur droit)

### Champs

* Tropopause
    * Représentation : Lignes solides représentant la hauteur de la tropopause au dessus du niveau moyen au niveau de la mer. Intervalles de 5 000 pieds; hauteurs exprimées en milliers de pieds. 
* Turbulence (Indice de cisaillement vertical : Déformation Vertical Shear Indexou DVSI).
    * Représentation : Lignes tiretées représentant le maximum de DVSI, dans la couche 400 à 200 hPa; contours à 30, 50, 150 et 240 DVSI.
        * __Rehaussement__ :
            * 0-50 DVSI : pas de rehaussement
            * 50-150 DVSI : pointillé léger
            * 150-240 DVSI : pointillé dense
            * Plus de 240 DVSI : pas de rehaussement

* __Note__: La tropopause, selon la définition de l'OMM.

### Pointage 

La base et le sommet de la couche de turbulence (DVSI) sont pointées, à des points de grille sélectionnés, en milliers de pieds au-dessus du niveau moyen au niveau de la mer; le chiffre du bas est la base et le chiffre du haut est le sommet.


## Flux de la quantité de mouvement ou tension en surface (panneau inférieur gauche)

### Champs

* Flux de la quantité de mouvement ou tension de surface.
    * Représentation : Lignes continues représentant les isoplèthes de la tension de surface à  0,5 Pa, 0,75 Pa, 1,5 Pa et  3,0 Pa.

### Note

La zone de 0,75 Pa à 1,5 Pa est hachurée horizontalement et représente la zone de turbulence mécanique modérée.  La zone de 1,5 Pa à 3,0 Pa est hachurée verticalement et représente la zone de turbulence mécanique intense.  La zone de plus de 3,0 Pa n'est pas rehaussée et représente la zone de turbulence mécanique extrême.

## Turbulence à moyenne altitude (panneau inférieur droit)

### Champs 

* Turbulence (Indice de cisaillement vertical: Deformation Vertical Shear Indexou DVSI). 
    * Représentation : Lignes tiretées représentant le maximum de DVSI, dans la couche 400 à 200 hPa; contours à 30, 50, 150 et 240 DVSI.
        * __Rehaussement__ :
            * 0-50 DVSI : pas de rehaussement
            * 50-150 DVSI : pointillé léger
            * 150-240 DVSI : pointillé dense
            * Plus de 240 DVSI : pas de rehaussement

### Pointage

La base et le sommet de la couche de turbulence (DVSI) sont pointés, à des points de grille sélectionnés, en milliers de pieds au-dessus du niveau moyen au niveau de la mer; le chiffre du bas est la base et le chiffre du haut est le sommet.

