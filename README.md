# Catalogue de données

Spécification du catalogue des jeux de données produits par une organisation.

## Contexte

Dans le cadre de [l'investigation du projet catalogage de la DINUM](https://jailbreak.gitlab.io/investigation-catalogue/synthese.html), des travaux ont eu lieu avec certaines parties prenantes sur un schéma "catalogue de données".

Le but de ce schéma est que les organisations puissent produire, partager et publier un catalogue de données dans un format commun et conforme à leurs pratiques respectives.

## Ressources

* [Définitions](https://jailbreak.gitlab.io/investigation-catalogue/synthese.html#/2)
* [Exemples de schémas](https://schema.data.gouv.fr/)

Analyse de l'existant :

| Schéma / modèle de données | Détails |
|----------------------------|---------|
| Arrêté sur les données de référence | [Legifrance](https://www.legifrance.gouv.fr/loda/id/JORFTEXT000034944648/)<br>9 champs |
| INSPIRE | [Spec PDF](http://inspire.ec.europa.eu/documents/Metadata/MD_IR_and_ISO_20131029.pdf) (page 10) |
| DCAT-AP | [Spec PDF](https://raw.githubusercontent.com/SEMICeu/DCAT-AP/master/releases/2.0.1/DCAT_AP_2.0.1.pdf)<br>4 champs obligatoires, 7 champs recommandés, 7 champs optionnels |
| Data Package | [Doc](https://specs.frictionlessdata.io/data-package/) |
| Catalogue simplifié | [Doc](https://scdl.opendatafrance.net/docs/schemas/catalogue.html)<br>Inspiré par DCAT-AP mais dédié aux collectivités<br>20 champs obligatoires |

[Mapping des modèles de données](https://lite.framacalc.org/9p8z-schema_catalogue_donnees) réalisé lors d'un atelier avec des parties prenantes, afin de faire converger les différents schémas et trouver un dénominateur commun.

## Etat des travaux

Ces travaux ont mené à l'écriture du [présent schéma tabulaire](./schema.json), écrit avec la spécification [Table Schema](https://specs.frictionlessdata.io/table-schema/).

Aperçu avec un [exemple pratique](./exemple-valide.csv) :

| titre                                | description                                                                                                                                                                                                                                                                                                                                                                                                          | mots_cles            | nom_orga                                                      | siret_orga     | id_alt_orga | service                            | si                    | contact            | date_pub   | date_maj   | freq_maj | couv_geo              | url                                                                            | format    | licence         |
|--------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------|---------------------------------------------------------------|----------------|-------------|------------------------------------|-----------------------|--------------------|------------|------------|----------|-----------------------|--------------------------------------------------------------------------------|-----------|-----------------|
| Arbres vivants inventoriés en forêt. | Données brutes de l'inventaire forestier correspondant à l'ensemble des données collectées en forêt sur le territoire métropolitain par les agents forestiers de terrain de l'IGN. Ces données portent sur les caractéristiques des placettes d'inventaire, les mesures et observations sur les arbres et les données éco-floristiques. Les coordonnées géographiques des placettes sont fournies au kilomètre près. | arbre,forêt,écologie | Institut national de l'information géographique et forestière | 18006701900430 | W343008792  | Service de l'inventaire forestier. | Inventaire forestier. | jean.martin@ign.fr | 2005-01-14 | 2019-05-28 | Annuelle | France métropolitaine | https://www.data.gouv.fr/fr/datasets/donnees-brutes-de-l-inventaire-forestier/ | CSV, XLSX | Licence ouverte |

Ce schéma de données est fortement inspiré de [DCAT-AP](https://joinup.ec.europa.eu/collection/semantic-interoperability-community-semic/solution/dcat-application-profile-data-portals-europe). DCAT-AP a été conçu dans le [paradigme "portail = catalogue"](https://jailbreak.gitlab.io/investigation-catalogue/synthese.html#/3/1), alors qu'on constate à travers l'investigation qu'il y a désormais dans les organisations des besoins liés au *data management* interne, en particulier le fait de favoriser la traçabilité du jeu de données jusqu'à sa source grâce à des métadonnées supplémentaires (personne contact, service producteur de données au sein de l'organisation, système d'information à partir duquel a été extrait le jeu de données).

Le présent schéma pourrait ainsi être pensé comme une extension française à DCAT-AP.

## Implémentation

- L'API de l'outil catalogage pourrait exposer les catalogues publics au format strictement conforme DCAT-AP en JSON-LD, afin de permettre notamment [le moissonnage par data.gouv.fr](https://doc.data.gouv.fr/moissonnage/dcat/) et [les moteurs de recherche](https://developers.google.com/search/docs/advanced/structured-data/dataset#approach).
- L'outil catalogage aurait une fonctionnalité permettant d’exporter un catalogue en CSV dans un format conforme au présent schéma tabulaire, afin de permettre notamment des usages dans [des logiciels comme Excel](https://jailbreak.gitlab.io/investigation-catalogue/synthese.html#/15/1).
