![alt_text](images/image1.png "image_tooltip")

```
Cadre de Cohérence Technique (CCT)

Volet  : Cloud π Native  à portée interministérielle

Version : Béta.Q2.2024
Date : 20/04/2024

Auteur : Direction du numérique Ministère de l’Intérieur
``````
![alt_text](images/image2.png "image_tooltip")![alt_text](images/image4.png "image_tooltip")



Cette version RFC (request for comment) vous permet de proposer vos commentaires de plusieurs manières:
- faire des issues
- utiliser le fichier de relecture proposé
[Fichier pour commentaires ](./gabarit-pour-commentaires.ods)
 et l’envoyer à : [dnum-architecture-entreprise@interieur.gouv.fr](mailto:dnum-architecture-entreprise@interieur.gouv.fr)

##


# 1 - Introduction

Ce présent volet, du cadre de cohérence technique Cloud Pi Native, s’adresse aux développeurs, architectes et en général aux acteurs se projetant dans la planification, l’élaboration et la maintenance de produits numériques basés sur la conteneurisation et Kubernetes. Il présente le cadre et les exigences qui permettent à une direction d’application de faciliter la construction d’application de qualité et l’accès à l’offre de service proposée.

Ce cadre est soutenu par la plateforme de service Cloud Pi Native, proposant un parcours simple et prédictif, limitant les frictions organisationnelles et mettant à disposition des configurations préconfigurées pour réduire les charges de travail et cognitives des équipes.

La construction de produits numériques robustes basés sur les principes agiles et DevSecOps permet une plus grande réactivité des équipes, permet grâce à la mise en place de cycle plus court à quelques semaines permet d’obtenir un meilleur feedback des usagers pour produire des produits numériques de qualité et sécurisé qui répondent au besoin.

Le cloud dit _native_, basé sur la technologie de conteneurisation et d’orchestration, tel que Kubernetes rend plus robuste et fluide la construction, le déploiement et l’exécution d’applications. Ces technologies sont adoptées massivement par l’ensemble des d’organisation et des développeurs.

L’ensemble de l’offre Cloud Pi Native intègre les composantes suivantes :

- L’utilisation de clusters kubernetes sur cloud public pour des cas d’usage standard ou un hébergement ministériel on-premises durcis, soit en tant que namespace as a service (ou clusters dédiés) jusqu’au niveau DR pour les cas d’usage sensibles ;

- une console adaptées autonomisant les projet, intégrant un service de construction DevSecOps d’image applicative conteneurisée, de gestion du code d’infrastructure, et un système gitops assurant le déploiement automatisé, sécurisé depuis l’internet ;

- un modèle de sécurité ( dast et sast ) ainsi qu’un dashboard dédié à l’amélioration en continue de la sécurité pour les projet, responsable sécurité des métiers et les acteurs centraux cyber;

- un corpus documentaire et d’exemples permettant l’autoformation ;

- un modèle de maturité pour permettre la progression et le coaching des équipes.

Ce document et les ressources associées permettent  à également pour objectif de :

- guider les concepteurs d’applications afin d’optimiser les architecture produites selon les normes industrielles rigoureuses, les meilleures pratiques DevSecOps et du Cloud Native tout en maintenant une capacité d’innovation ;

- mettre à disposition un référentiel d’exigences favorisant les bonnes pratiques et la conformité ;

- diminuer ressources consommées ( financière, RH, énergétique) par la réduction de la  quantité de code à produire et la modularité et l’efficience des architecture applicatives ;

- maintenir un niveau de compatibilité minimal entre les offres cloud ;

- fluidifier les déploiement, l’homologation en continu, le maintien en qualité ;

- mettre en place un modèle de responsabilité et de collaboration adapté ;

- disposer d’une trajectoire soutenable pour ceux en charge de maintenir l’offre.

Les  différents documents qui constituent le cadre de cohérence technique  :
- [Lien vers le corps descriptif du CCT ](./cct-cloud-native.md)
- [Lien vers l'annexe présentant les normes applicables](./cct-normes.md)
- [Lien vers la liste des exigences associées au CCT ](./cct-exigences.md)
- [Lien vers le glossaire](./cct-glossaire.md)

