# Schéma Catalogue de données

Spécification du catalogue des données produites par une organisation.

## Contexte

Le service `catalogue.data.gouv.fr` déployé par la DINUM et s'appuyant sur [un outil de catalogage de données](https://github.com/etalab/catalogage-donnees) permettra aux ministères et aux opérateurs sous leur tutelle de créer, gérer et ouvrir leurs catalogues.

Le schéma ici présent a vocation à leur permettre de produire, mettre à jour et publier un catalogue de données dans un format commun et conforme à leurs pratiques respectives.

## Ressources

- [Définitions](https://jailbreak.gitlab.io/investigation-catalogue/synthese.html#/2)
- [Exemples de schémas](https://schema.data.gouv.fr/)

Analyse de l'existant :

| Schéma / modèle de données          | Détails                                                                                                                                                                   |
| ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Arrêté sur les données de référence | [Legifrance](https://www.legifrance.gouv.fr/loda/id/JORFTEXT000034944648/)<br>9 champs                                                                                    |
| INSPIRE                             | [Spec PDF](http://inspire.ec.europa.eu/documents/Metadata/MD_IR_and_ISO_20131029.pdf) (page 10)                                                                           |
| DCAT-AP                             | [Spec PDF](https://raw.githubusercontent.com/SEMICeu/DCAT-AP/master/releases/2.0.1/DCAT_AP_2.0.1.pdf)<br>4 champs obligatoires, 7 champs recommandés, 7 champs optionnels |
| Data Package                        | [Doc](https://specs.frictionlessdata.io/data-package/)                                                                                                                    |
| Catalogue simplifié                 | [Doc](https://scdl.opendatafrance.net/docs/schemas/catalogue.html)<br>Inspiré par DCAT-AP mais dédié aux collectivités<br>20 champs obligatoires                          |

[Mapping des modèles de données](https://lite.framacalc.org/9p8z-schema_catalogue_donnees) réalisé lors d'un atelier avec des parties prenantes, afin de faire converger les différents schémas et trouver un dénominateur commun.

## Etat des travaux

Ces travaux ont mené à l'écriture du [présent schéma tabulaire](./schema.json), écrit avec la spécification [Table Schema](https://specs.frictionlessdata.io/table-schema/).

[Exemple de fichier catalogue (une seule ligne) conforme au schéma.](https://validata.fr/table-schema?input=example&schema_url=https://github.com/etalab/schema-catalogue-donnees/raw/master/schema.json&url=https://github.com/etalab/schema-catalogue-donnees/raw/master/exemple-valide.csv).

Ce schéma de données est fortement inspiré de [DCAT-AP](https://joinup.ec.europa.eu/collection/semantic-interoperability-community-semic/solution/dcat-application-profile-data-portals-europe). DCAT-AP a été conçu dans le [paradigme "portail = catalogue"](https://jailbreak.gitlab.io/investigation-catalogue/synthese.html#/3/1), alors qu'on constate à travers l'investigation qu'il y a désormais dans les organisations des besoins liés au _data management_ interne, en particulier le fait de favoriser la traçabilité du jeu de données jusqu'à sa source grâce à des métadonnées supplémentaires (personne contact, service producteur de données au sein de l'organisation, système d'information à partir duquel a été extrait le jeu de données).

Le présent schéma pourrait ainsi être pensé comme une extension française à DCAT-AP.

## Implémentation

- L'API de l'outil catalogage pourrait exposer les catalogues publics au format strictement conforme DCAT-AP en JSON-LD, afin de permettre notamment [le moissonnage par data.gouv.fr](https://doc.data.gouv.fr/moissonnage/dcat/) et [les moteurs de recherche](https://developers.google.com/search/docs/advanced/structured-data/dataset#approach).
- L'outil catalogage aurait une fonctionnalité permettant d’exporter un catalogue en CSV dans un format conforme au présent schéma tabulaire, afin de permettre notamment des usages dans [des logiciels comme Excel](https://jailbreak.gitlab.io/investigation-catalogue/synthese.html#/15/1).
