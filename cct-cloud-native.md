![alt_text](images/image1.png "image_tooltip") ![alt_text](images/image2.png "image_tooltip")

```
Cadre de Cohérence Technique (CCT)

Volet  : Cloud π Native à portée interministérielle

Version : Béta.Q2.2024
Date : 20/04/2024
Auteur : Ministère de l’Intérieur
```

## TABLE DES MATIÈRES

<br>**1 - Guide d’utilisation rapide**
<br>**2 - Le contexte, les enjeux, la vision**
<br>**3 - Principes généraux cadre Cloud Native**
<br>Les configurations d’hébergement prises en compte
<br>Gestion des non-conformités, dérogations et contribution
<br>Le modèle organisationnel, de responsabilité et de collaboration Cloud Native
<br>Préconisations générales d’architecture et technique
<br>Des spécificités à prendre en compte sur la création des conteneurs
<br>Des spécificités à prendre en compte sur la topologie réseau et les ouvertures de flux
<br>Des spécificités à prendre en compte autour de la qualité et de la sécurité des applications
<br>Modèle d’intégration d’une application dans le cadre Cloud Native
<br>**4 - Présentation de l’offre interMinistérielle Cloud Pi Native et de ses évolutions pressenties**
<br>Les magasins de composants kubernetes et d’image de base
<br>**5 - Référentiel d’exigences et modalités d'usage**
<br>**6 -  Annexes**


# 2 - Le contexte, les enjeux, la vision

**Audience : ce paragraphe s’adresse à tout acteur considérant l’usage de l’offre Cloud Pi Native du ministère de l’intérieur, il présente les principes fondateurs.****Le cloud : des nouvelles possibilités techniques, une collaboration étendue des acteurs pour répondre aux enjeux d’un contexte exigeant, incertain et accéléré.**

À travers sa doctrine « Cloud au centre », l’État encourage l’ensemble des acteurs publics à se saisir de son potentiel afin de développer une nouvelle génération de services numériques de qualité et qui répond au besoin dans un cadre de normes juridiques adapté à l’usage. Cela répond notamment au besoin accru d’agilité et d’efficience de l’administration.

Le Cloud est une approche d’accès à l’infrastructure d’hébergement à travers une interface standardisée et rendant abstraite et normalisée les technologies sous-jacentes. Cette abstraction permet une automatisation poussée, supprimer les frictions organisationnelles, les non-qualités et lenteurs induites par des opérations manuelles. L’infrastructure est pilotable par du logiciel et donc automatisable avec des processus reproductibles.

La technologie Cloud Native fait référence à l’usage de la conteneurisation et Kubernetes. Kubernetes
est une technologie d’orchestration de conteneur issue des travaux, il y a plus de 15 ans de Google, mise à disposition en open source et gérée par la fondation linux, permettant de simplifier le flux de production logiciel et rendre encore plus efficace et sécurisée l’usage des infrastructures techniques, la résilience des hébergements et apporter une souplesse organisationnelle accrue. Les grands services de l’internet s'appuient sur cette technologie, elle permettent une résilience extrême et permet d’absorber un trafic extrêmement important.

Les architectures des applications se simplifient avec une abstraction de plus en plus grande de l’infrastructure avec notamment la montée en puissance de services managés, functions-as-a-service dans l’objectif recherché de diminuer la quantité de code produite ( et donc de réduire les bugs et la complexité de la maintenance ) ainsi que grâce à une standardisation industrielle poussée et la conteneurisation, permet de réduire la charge des équipes, déchargée de nombreuse problématique de gestion de l’infrastructure de leur application et du déploiement.

L’ensemble des organisations ayant mis en œuvre cette technologie telles que EDF, Orange, des services de vente en ligne, des Banques, Airbus, Urssaf, etc… ont vu également leurs efficiences de l’usage du numérique augmenter, il y a un *avant et un après* Kubernetes.

Le ministère de l’intérieur, l’un des premiers acteurs étatiques à avoir proposé une offre Cloud il y a plus de 5 ans, étend son offre de service, en proposant l’offre Cloud Pi Native combinant une offre d'hébergement kubernetes sécurisée jusqu’au niveau DR. Cette offre est accompagnée d’un modèle DevSecOps permettant une fluidité organisationnelle accrue et un renforcement de la qualité des solutions numériques.

Les approches cloud, devops et l’agilité ont progressivement permis de concilier des postures antagonistes : les développeurs ayant besoin de pouvoir déployer fréquemment, et l’exploitation ayant au contraire besoin de stabilité et de diminuer les risques liés au changement. La clé réside dans une collaboration étendue de tous les acteurs en prenant compte de la sécurité à toutes les étapes en continue : le DevSecOps.

**Une évolution des pratiques pour un numérique efficient et éco-responsable et réactif**

Les contraintes s’accentuent sur la production de services numériques, le standard de qualité général a augmenté massivement avec les acteurs du net et industrielle qui produisent des solutions ergonomiques, sécurisées qui montent à l’échelle facilement. Un fossé important s’est creusé entre l’efficience du numérique ‘legacy’ et ce monde moderne.

L’environnement change rapidement, il devient incertain, il faut réagir de plus en plus rapidement, la pression augmente sur la production de solutions numériques ergonomique, nécessitant des cycles raccourcis, la prise en compte de l’éco responsabilité, de l’accessibilité et le maintien d’un haut standard de qualité et de sécurisation.

Seul un changement majeur de pratiques s’appuyant sur l’opportunité du Cloud Native et du DevSecOps permettent de satisfaire ce nouveau standard d’exigences.

Le mode produit et l’agilité sont indispensables en complément de l’utilisation du cloud, extrait de la doctrine cloud au centre:

Citation issue de la doctrine cloud au centre de l’État : 
>   “ *L’adoption du cloud doit s’accompagner de celle des pratiques associées à l’excellence dans la production de services numériques (proximité entre métiers et équipes informatiques, scalabilité, agilité, « devops », « continuous delivery » qui sont les garants de l’adaptation des produits à leurs utilisateurs) ;  “*

**Les principales caractéristiques du modèle opérationnel Cloud Native:**

****

Le fonctionnement évolue vers un partage des responsabilités dans la chaîne de production orienté vers la livraison du service vers les usagers.

**L’équipe projet intégrée (ou équipe produit intégrée) voit ses prérogatives étendues:**

- Elle est organisée autour du produit numérique livré. Elle fonctionne en modalité intégrée et de manière autonome en lien avec la vision et les contraintes fixées.

- Elle est composée de développeurs, architectes, ergonome (ux-design), juriste, gestionnaire du changement, etc… orchestrée par le product owner et généralement facilité par un coach / scrum master agile.

- Elle est focalisée sur l'ergonomie, la qualité et la performance de la solution mise à disposition des usagers. C’est le modèle «You build it, you run it, you support it ». (vous l’avez construit vous l’opérez )

Temporairement ou de façon permanente selon la taille de produit, une équipe d’aide, appelée “service team”, peut être chargée, au sein de l’équipe produit, de mettre en place l’automatisation et les environnements de travail et de production
.

Cette dernière doit être aguerrie à ces technologies et l’offre cloud pi native.

**L’hébergeur assure quant à lui**, la mise à disposition d’une offre de service hautement disponible et sécurisée. L’usage de l’offre est réalisé via une console, une interface technique normée (API), une documentation et des exemples accélèrent la prise en main.

Il assure également la fourniture de services d’abstraction tels que des services managés ou fonctions as a service, un pipeline devsecops etc…

**L’équipe intégrée est autonome et travaille sans échange avec l’hébergeur**. La console mise à disposition assure ce lien avec une documentation associée. L’ensemble des opérations réalisées manuellement auparavant lors des étapes d’élaboration sont complètement automatisées. Le code logiciel est testé en permanence et automatiquement par un outillage : l’orchestrateur DevSecOps.

Pour assurer la qualité du code, plusieurs principes sont mis en œuvre, une couverture de test (100% sur le back-end), l’analyse statique du code, l’analyse récursive de vulnérabilité des composants importés (librairie, images ), des tests de sécurité et de performances, tests spécifiques liés à des besoins de vérifications particulières.

L’équipe de développement est prévenue au plus tôt par l’orchestrateur DevSecOps en cas de non-qualité. L’orchestrateur offre des options techniques pour intégrer les retours dans le flux de travail du développeur afin de procéder à la correction au plus tôt des anomalies, cette modalité s’appelle “shift-left”. *In fine*, seul un logiciel ayant atteint le niveau de qualité fixé peut être déployé.  

Les développeurs assurent continuellement la qualité et la sécurité du code produit, la non-régression et l'absence de vulnérabilité soutenus par l’outillage mis en place, la chaîne devsecops, les environnement de codage (IDE) et gestionnaire de code deviennent de plus en plus en plus performant et identifient dès l’écriture ou l’intégration du code les erreurs d'algorithmes ou si un secret (mots de passe, clé API)  est laissé dans le code ou aide le développeur à mieux produire du code optimisé via l’utilisation de l'intelligence artificielle.

Les architectures sont modulaires et les composants internes ainsi que les interfaces entre applications sont découplées, c’est à dire rendus indépendants techniquement et organisationnellement via des interfaces normées (API). Cela permet la maintenance et les  évolutions indépendantes entre composants. Ce découplage contribue fortement à réduire le coût des changements et faciliter les transitions technologiques en cas d’obsolescence.

La conception de l’architecture, le choix des langages sont faits pour une efficience de l’usage des ressources d’infrastructures et également sur l’impact sur le poste de travail.

La conteneurisation, l'élasticité dynamique de la solution d'orchestration de conteneurs kubernetes, la mutualisation des infrastructures physiques soutiennent fortement cette  efficience.

Le non-respect de ce principe de modularité a été identifié par la direction interministérielle du numérique comme l’une des causes d’échec des grands programmes de l’État. La modularité, l’indépendance technique et organisationnelle des modules lors du déploiement, permettent de réduire la taille des déploiements ce qui contribue à réduire les risques et fluidifier les mises en production. Les déploiements peuvent ainsi être rendus transparents pour  des usagers et les retours arrière éventuels sont  facilités. Il est ainsi possible de déployer en confiance, plusieurs évolutions par jour si nécessaire.

L’automatisation permet de  mieux contrôler et rendre les actions prédictibles, faciliter la reprise en cas d’incident et minimiser les coûts de maintien en conditions opérationnelles et de sécurité des applications. Plus aucune intervention manuelle n’est effectuée sur les environnements ce qui permet de réduire la variance, les non-qualités, et aussi de (re)construire très rapidement des plateformes.

In fine, la conception doit s’inscrire dans une démarche d’éco-conception et de sobriété numérique des conceptions (green IT) permettant un usage plus efficient des ressources  qu’elles soient RH, financières ou énergétiques. L’État devant être exemplaire
.

# 3 - Principes généraux cadre Cloud Native

**Audience : ce paragraphe s’adresse à la communauté des concepteurs et architectes solutions, le lecteur est réputé compétent et formé sur les sujets abordés .**

Le cadre de cohérence technique régule et normalise les différents domaines associés à l’élaboration et au maintien des ressources partagées nécessaires à la mise à disposition de solutions numériques de qualité répondant au besoin. Il s’assure que l’ensemble peut-être mis en œuvre de manière cohérente avec une consommation minimisée des ressources : financière, RH et écologique. Il recommande ou fixe les mesures permettant d’atteindre l’objectif, tout en favorisant l’innovation, la prise en compte de l’obsolescence régulière des technologies et la manœuvre RH nécessaire (formation continue, recrutement …)

Le volet du CCT Cloud Native du ministère de l’intérieur, hérite de normes industrielles, interministérielles et européennes. La portée de ce document est interministérielle, il a fait l’objet d’échanges avec la direction interministérielle du numérique et des ministères primo-accédants.

Pour le ministère de l'Intérieur, il encadre la conception et l’hébergement d’applications qu’elles soient hébergées dans les datacenters du ministère ou bien à l’externe sur des clouds publics. Ce volet s’applique notamment lors de la conception d’une nouvelle application ou une évolution significative d’une application existante. (cf Doctrine Cloud au centre)

Pour les autres entités étatiques, ce volet sert de présentation de bonnes pratiques et présente les conditions générales d’utilisation de l’offre Cloud Pi Native.

Ce document ainsi que le référentiel d’exigences sont annexés aux dossiers de consultation des entreprises. La portée administrative étant précisée par le règlement de consultation (RC) du marché lui-même, typiquement le RC et le Cadre des clauses administratives particulières (CCAP) peuvent exclure administrativement un candidat en cas de non-respect des exigences P primordiales. (hors dérogation soumise, instruite et accordée).

D’autres référentiels d’exigences ou des guides peuvent être applicables ou conseillés. voir plus loin le chapitre sur les cadres de normes supérieures.

**Offre de service Cloud π Native :**

Concerne la description de l’offre de service managé d’infrastructure Cloud **π** et d’une chaîne DevSecOps assurant l’homologation en continu et le déploiement en production. Cf. présentation de l’offre plus loin dans ce document. Cette offre évoluera selon les demandes et financement disponible vers services d’abstraction de l’infrastructure, tel que service managés, fonction, etc…

**Poste de travail agent :**

Dans le cadre d’une application rendue accessible sur le poste de travail de l’agent, le lecteur est invité à se conformer également au volet *Environnement Numérique de Travail*, notamment sur les aspects d’intégration au SSO et la politique des navigateurs.

**Ouverture des données :**

Sur la thématique de l’ouverture et de la circulation de la donnée, le projet est invité à se mettre en conformité avec le volet idoine. Cela concerne notamment le référencement des objets métiers dans le référentiel de cartographie des données et la mise à disposition d’une facilité technique d’accès à la donnée basée sur un standard d’échange de type API.

L’ensemble des acteurs de l’État est invité à faire circuler la donnée au profit d’une simplification du fonctionnement des administrations et d’un service public ergonomique et proactif .  (cf rapport Bothorel, lois CRPA et 3DS, … )

## Périmètres du CCT et configurations prises en compte

Ce CCT concerne l’usage de l’offre Cloud Pi Native dans les configurations précisées ci-dessous.

Le ministère de l’intérieur dispose de plusieurs capacités d’hébergement d’application. Ces offres peuvent être historiques et liées à une entité  (ex: Sgami, ANTS)  ou centrales.

Les offres d’hébergement centrales sont découpées en plusieurs catégories  :

- **Physique ou virtualisées** généralement de type VMWAre tel qu’Isocèle ( DTNUM), STIG (ANFSI). Cette offre est accessible qu’au MIOM et seul l’exploitant gère la plateforme et les actes d’intervention techniques via Ticketing ITMS

- **Offre Cloud Pi** : offre Iaas basée sur OpenStack. La gestion interne des ‘tenants’ est à la main du développeur, le reste via ticketing. Note : Le développeur gère son outillage projet en autonomie

- **Offre Cloud Pi Native** ( objet de ce volet de CCT ) :  offre s’appuyant sur Cloud Pi, avec un espace d’exécution sur kubernetes, des services d’accélération de construction applicatif en sus.

Les configurations suivantes sont prises en compte par ce volet Cloud (Pi) Native du CCT.

- Hébergement sur les clusters kubernetes managés par le ministère de l’Intérieur, jusqu’au niveau « donnée restreinte » ;

- Hébergement sur un cluster kubernetes externe au ministère, compatible avec la sensibilité des données manipulées ;

- Hébergement sur un cluster kubernetes dédié et géré par l’application;

- Une approche hybride multi-clusters ( plusieurs environnements de production on prem ou cloud public ).

**Pour l’ensemble de ces configurations l’usage de la chaîne DevSecOps managée par le Ministère de l’Intérieur est impératif. (hors cadre dérogatoire accordée)**

## Gestion des non-conformités, dérogations et contribution

L’évolution rapide des technologies cloud peut conduire à ce que le cadre CCT restreigne l’innovation. Il est également souhaité, pour éprouver le modèle, de notifier le département architecture d'entreprise du Ministère de l'intérieur au plus tôt des éventuelles impossibilités ou limitations remarquées. Les directions d’applications ou les organisations utilisatrices peuvent contribuer, via un échange préalable, à enrichir les fonctionnalités de l’offre ou du cadre lui-même. Sur l’offre la contribution est effectuée directement sur le repository open source de la solution via un pull request.

En cas de non-conformité au CCT ou absence de contribution à l’offre, une demande de dérogation dûment motivée sera formulée à l’avance par la direction d’application. Seule la notification de la décision permet d’amender le besoin de conformité au cadre, temporairement ou de manière pérenne dans le cadre d’une dérogation. Dans le cadre d’une dérogation, la direction d’application prend à sa charge le surcoût complet de possession. ( formation, homologation, personnel assurant la tme, etc… )

Lors de l’utilisation du cadre et de l’offre Cloud PI Native, toute organisation souhaitant décliner ce cadre dans un document de norme inférieur pour un besoin propre est invitée à référencer la dernière version de ce document en l’état.  Dans la hiérarchie des normes, une instruction de niveau inférieur ne peut entrer en conflit ou contredire ce présent document.

## Le modèle organisationnel, de responsabilité et de collaboration Cloud Native

L’architecture, le modèle de responsabilité et d’organisation à mettre en place est orienté pour maximiser la qualité, la sécurité, la fluidité opérationnelle et l’évolutivité du produit en  tirant parti au maximum des possibilités offertes par la technologie kubernetes, un flux de production DevSecOps et une collaboration étendue entre les acteurs.

**L’élargissement de la responsabilité du développeur et de l’équipe produit**

La responsabilité de l’équipe produit est élargie dans le cadre Cloud Native. Elle élabore et exploite une solution qui répond au besoin métier généralement une automatisation d’un ou plusieurs processus métiers . L’équipe s'assure de la qualité et de la disponibilité du service rendu à l’usager selon le précepte : « You build it, you run it ». L’équipe s’organise de façon  intégrée, si nécessaire avec de l’externalisation, pour couvrir l’ensemble des aspects nécessaires de la conception à l’exploitation des produits.

Le développeur, en particulier, met à disposition d’un point de vérité du code sous la forme d’un ou plusieurs dépôts de code logiciel fonctionnel et d’infrastructure. Il met en place un flux intégré et continu de production en s'appuyant sur un orchestrateur primaire DevSecOps qu’il construit et opère.

Le développeur initialise et supervise le pipeline de l’orchestrateur secondaire opéré par le ministère de l’Intérieur (cf plus loin sur la configuration de l’offre Cloud Pi Native). Il intègre les étapes de vérification de sécurité génériques imposées par le ministère et spécifiques issus de la démarche d’homologation.

L’ensemble combiné des orchestrateurs primaire et secondaire assure la fonction d’homologation et de déploiement en continu du produit numérique.

Dans le cas de la détection d’une non-qualité critique, telle une vulnérabilité critique, la progression du déploiement est bloquée, le développeur est prévenu en temps réel et doit corriger au plus tôt les défauts remontés. Cette approche permet de garantir un niveau de qualité, évite des régressions et maintient la dette technique au niveau le plus bas.

Sur le plan organisationnel le développeur met généralement en place :

- un contrôle de qualité au plus tôt, par exemple par un assistant et la revue de code ;

- l’agilité avec des itérations courtes de constructions et de vérification des usagers ;

- le découpage des livraisons en lot de taille de réduite ;

- la mise en place d’une culture de collaboration étendue et des pratiques intégrant la sécurité à toutes les étapes.

**La répartition des responsabilités s'établit de la manière suivante  :**

**L'équipe produit intégrée :**

- est responsable de l’application, de la qualité du code  et du bon fonctionnement de l’application pendant <span style="text - decoration: underline;">l’ensemble du cycle de vie de l’application. </span>

- est responsable de définir et d’ajuster l’infrastructure en s’appuyant sur l’élasticité du cloud.(sur la base de l’offre Cloud adaptée selon la sensibilité des données)

- s'appuie sur les patterns applicatives et services managés mis à disposition, les magasins de charts helms et des *operators*disponibles. Il est déconseillé, par exemple, de repackager une base de données alors qu’un *operator*, un chart ou un service managé est disponible. ( simplification et systématisation du mcs )

- fournit un code de qualité exempt de défaut d'algorithmes, de qualité et de vulnérabilité ;

- met en œuvre le flux de production, logiciel local permettant d’assurer la production et la démonstration d’un code de qualité exempt d’anomalie fonctionnelle, de non-qualité et de vulnérabilité, notamment dans les librairies importées ;

- pose les normes de développement des langages utilisés ;

- met en place des pratiques DevSecOps visant un maintien de la qualité dans le temps avec les composantes suivantes ( cf outillage DevSecOps) :

- test driven development ;

- couverture de test unitaire à 100% du back-end de l’application ;

- couverture significative des tests du front de l’application ;

- analyse statique de qualité du code ;

- analyse récursive des vulnérabilités des librairies importées ;

- utilisation exclusivement d’images sources maintenues en condition de sécurité et certifiées (distribution LTS) ;

- conception des tests d’intégration en sandbox ;

- fourniture des outils nécessaires à la remontée de l'état de santé des briques applicatives destinées à fonctionner en production (healthcheck) ;

- fourniture des indicateurs nécessaires au suivi en temps réel de la qualité en condition opérationnelle de sa solution (exports prometheus) ;

- exploitation des logs remontés.

- met en place un hébergement sur une plateforme kubernetes afin d’assurer la démonstration du bon fonctionnement de l’application avec la solution qu’il préfère soit internalisée (avec un moyen de mener des démonstrations) ou sur cloud public.

- met en œuvre l’intégration technique et organisationnelle avec la chaîne DevSecOps de l’offre Cloud Pi Native et initialise le flux logiciel  global (cf plus bas).

- maintient un point de vérité du code logiciel ainsi que celui du code d’infrastructure. Celui-ci est accédé par la chaîne DevSecOps étatique, la sécurisation d’accès issus par token.

- est responsable de la surveillance de l’ensemble des pipelines, y compris pour celui géré côté ministère.

- met en place une intégration du flux de retour d’anomalie “shift-left” des orchestrateurs afin de permettre une correction au plus tôt des anomalies.

- effectue l’apprentissage comportemental du firewall applicatif Web (WAF) vis-à-vis de l’application dans le cadre fixé par le ministère. (anticipation avant la mise en production)

- est invité à mettre en œuvre ce pipeline au plus tôt dans le processus de réalisation.

**Notes :  ( cf exigences CCT )**

**L’équipe de développement respecte les règles suivantes permettant une qualité de code en progression et un maintien de la sécurité :**

- minimise la portion spécifique de code développés en s’appuyant sur le catalogue des services proposés. (revoir régulièrement)

- met en place une couverture de test unitaire complète du back-end  ( et fourni les moyens de vérification automatisé à la chaîne secondaire )

- mener une analyse de code systématique le plus tôt possible ( les langage et IDE modernes fournissent des fonctions de ce type )

- mener une analyse de CVE des dépendants importées et apporter des corrections.

L’équipe intégrée met en œuvre une activité continue de refactoring du code produit. Ainsi, la qualité du code ne peut pas être décroissante.

**Elle fournit les preuves** que des tests de sécurité, de qualité, de robustesse des algorithmes ont été mis en œuvre, et qu'ils n'ont pas remontés de vulnérabilités ou d'erreurs majeures. En s’appuyant notamment sur les logs des analyses des outils de la chaîne primaire. Elle fournit la preuve (ex: le document) des normes de développement et pratiques permettant de maîtriser la qualité du code produit. ( refactoring, peer review, etc.. )

Note : l’équipe s’assure qu’après le dernier déploiement stable de l’application, toutes nouvelles vulnérabilités critiques et importantes seront détectées et corrigées. En cas de non correction des anomalies dans un délai de plusieurs mois et surtout si l’application est exposée sur internet, l’hébergement de la solution pourra être suspendu pour maintenir en intégrité les données.

**L’****exploitant**** Ministériel de la console et de l’orchestrateur DevSevOps** :

- Il assure de la disponibilité et de la qualité de fonctionnement de la chaîne DevSecOps et maintient à jour la documentation sur le fonctionnement des interfaces et assure les évolutions fonctionnelles ;

- Il assure les retours d'anomalies "shift-left" lors des opérations de déploiement continu. L'intégration et leurs traitements sont à la charge du Concepteur / développeur ;

- Il contribue à la mise en place et l’évolution du catalogue d’operator Kubernetes, de charts helm et du référentiel de pattern de référence;

- Il est également en lien avec les autorités d’homologation afin de s’assurer que l’ensemble est en condition d’assurer la protection d’ensemble;

- Il intègre les propositions d'évolution “pull request” proposée en fonction de son plan de charge et d’une négociation préalable.

- Il fournit la documentation dont les éléments d’orientation ou d’aide à la migration permettant au développeur de s’orienter vers l'opérateur cloud qui hébergera son produit. ( cela dépend également des décisions projets ou d’homologation )

**L’opérateur ****Cloud ministériel ou Public** :

ll assure le maintien en condition de disponibilité et de sécurité de l’offre d’hébergement, l’interface API de management, la console, la gestion capacité et les offres de services managées.

Dans le cas de l’offre ministérielle du ministère de l’Intérieur, plusieurs services additionnels peuvent être consommés, tel que la supervision applicative ou de sécurité, la fourniture de poste d’administration sécurisés.

Le Cloud PI est constitué de plusieurs régions ( elle même constituées de plusieurs centres de calculs ) en zones de sensibilité usuel et DR.

Chacune des régions peuvent faire l’objet d’une affinité ou restriction de services, sur la nature des données, des typologies de projets, ministériels et interministériel, chaîne de SecOps secondaire;  etc…

La gouvernance du produit ‘Cloud Pi Native” à portée interministérielle et ministérielle définit la politique d’ensemble, cette dernière traite d’aspects tel que : restriction ou affinité d’accès aux régions, projets, chaine secondaire ;

- politique de données définie dans l'extension de la définition de "données restreintes" ;

- la capacité en matière de ressources nécessaires à héberger de nouveaux projets ;

- la localisation géographique et le nombre de centres de calculs constituant sa région ;

- les services mis à disposition ;

- les possibilités d'interconnexion réseau avec d'autres systèmes;

La version courante de l’offre et la politique d’usage est mise à disposition sur portail et notamment vers l’utilisateur lors de la connexion à la console. La version courante est présentée dans les grandes lignes au paragraphe 4.

Des pratiques complémentaires sont introduites dans la configuration Cloud Native :

**Le “GitOps”,**contraction de git et opération, est indispensable à la gestion des applications Cloud Native avec Kubernetes. Ce mode d’organisation du code d'infrastructure permet de maîtriser la description de l’infrastructure de production avec les mêmes pratiques de revue collaborative que celle du logiciel. Il est par exemple strictement interdit de faire des modifications «à la main » sur l’environnement de production, toute variation est supprimée, l’infrastructure réelle est strictement celle décrite par les fichiers d’infrastructure.

Le **“shift-left”**(vers la gauche du processus de développement) fait référence à la remontée le plus tôt possible vers le développeur des anomalies identifiées par la chaîne de déploiement et de vérification DevSecOps. Ce flux est notamment mis en œuvre depuis la chaîne secondaire.

**Présentation du cycle d’usage de l’offre pour les directions d’applications:**

**Phase d’initialisation du projet**

- Le développeur initialise l’environnement de développement, il est autonome pour les choix techniques, il respecte les exigences organisationnels et de processus automatisé permettant de maintenir une qualité constante ;

- Le développeur décide de l’infrastructure d’hébergement en fonction des contraintes sur les données et la liste des options autorisées et maintenue par la Dinum et l’ANSSI en lien avec la doctrine Cloud au centre, notamment  :  Cloud Pi, cloud externe de confiance ou plateforme dédiée (si besoin spécifique)

- Le développeur commande, (signature de convention), initialise l’espace projet au ministère et configure selon son choix d’infrastructure les environnements désirés. Il récupère les clés techniques nécessaires à l’intégration des pipelines.

- Le développeur effectue l’intégration des pipelines, cf  labels (2) , et (4) si l’infrastructure est externe.

- Il vérifie que l’ensemble du pipeline est opérationnel à partir d’un code d’exemple fourni de type “hello word”.

**Principe de fonctionnement du pipeline d’ensemble ( chaînes primaire et secondaire )**

![vue du pipeline d'ensemble](images/NsR_Image_2.png)

- **[1]** Le code logiciel ainsi que celui de description des infrastructures sont produits au sein de l’espace du développeur/concepteur, généralement en externe au Ministère de l’Intérieur.

- **[2a]** **[2b]**Une interface bi-directionelle entre l’espace du concepteur / développeur et celui de DSO permet en push-pull à la chaîne secondaire de récupérer automatiquement l’ensemble du code et des dépendances nécessaires.

- Le développeur déclenche par appel API les services de synchro /  build / deploy. ( il n’y accède pas directement sauf via un Bastion)

- **[3a][3b]** La chaîne d’orchestration DevSecOps effectue la récupération du code, des tests de qualité du code, scan de vulnérabilité des dépendances, la reconstruction, les tests de nos régressions, des tests d’homologation, vérification des manifests / charts etc… au regard des politiques de sécurité et dépose les images certifiées sur la registry de la chaîne ainsi que le code d’infrastructure.

- Le concepteur/développeur accède à un retour d’information détaillée sur le succès ou sur les éventuels défauts, lors du build, deploy de l’application par DSO. ( via message ou webhook )

- **[4]** : La console provisionne si nécessaires les environnements en ‘poussant’ les ressources nécessaires une foi (secrets, application.yaml (argo), certificats, etc... )

- **[5]** : L’infrastructure vérifie régulièrement les changements sur le dépôt d’infrastructure (ou déclenchement forcé par API) et synchronise l’environnement à la cible visé et opère une bascule blue-green transparente, cf ArgoCD  ( si échec l’environnement de prod reste inchangé )

- **[6]** : Le développeur accède à un proxy d’observation du fonctionnement de l’application

- Note : Les développeurs n'accèdent pas directement à la production. Seuls les administrateurs habilités peuvent y avoir accès via bastion.

##

## Préconisations générales d’architecture et technique

Ce chapitre précise les aspects importants liés à l’usage de kubernetes dans le cadre du ministère de l’intérieur.  Il est attendu que les acteurs soient correctement formés à la solution kubernetes et se maintiennent à jour. La technologie évoluant rapidement.

Le fondement des normes techniques est issu du cadre “Cloud Native”, largement accepté et appliqué au sein de l'État et le secteur privé, tel que les “15 factors”.

C’est le respect de ces normes qui permet à la fois d’adresser les enjeux de performance en termes de vitesse de livraison et de qualité de service, mais aussi de normaliser les applicatifs pour une meilleure évolutivité et maîtrise de la dette technique. Enfin, elles assurent une intégration fluide au sein des systèmes d’information Ministériels.

Un des principes cœurs est de laisser un certain degré de liberté au concepteur/développeur sur le fonctionnement interne de son application. Au contraire, les intéractions avec les autres applications et services seront particulièrement contraintes.

Il est à noter qu’uniquement la plateforme d’orchestration de conteneurs Kubernetes est considérée dans le cadre de ce cadre de cohérence, celle-ci étant considérée comme l’état de l’art, et open-source de surcroît.

À propos de la solution mutualisée d’hébergement Cloud π Native et de l’ergonomie pour le développeur

La philosophie générale est de balancer la réduction de la surface d'attaque cyber et l'ergonomie indispensable pour le développeur. La réponse définitive ne peut être que celle éprouvée en run, nous livrons ici une intention qui doit être rodée opérationnellement.

- Sur les **environnements côté “primaires”**, le développeur est (doit être) maître 'root,'  il les maîtrise et les utilise pour son besoin de débogguer tester des choses, etc… l’administration n’intervient pas ici.

- Sur les éventuels **d'environnement hors production côté secondaire au MI**, l’environnement est dédié au développeur il dispose d’un accès root à sa plateforme selon les règles de la PSSI applicables. ( voir plus loin )

- Sur**l'environnement de production côté MI,**les développeurs n'accèdent pas directement, cet accès s’effectue via une console dédiée et un flux “gitops”. ( via l’usage d’ArgoCD). L'accès à la production nécessiteune accréditation renforcée et adaptée et un poste 'rouge' ( niveau habilitation SD ).

- Sur**l'environnement de production chez un hyperscaler public,** le développeur gère sa plateforme. Généralement, il met en place un modèle d’opération réduisant les accès à la plateforme de production aux seuls administrateurs habilités.

**Notes :**

A propos de l’accès à des ressources d’environnements d’exécution situé côté administration, la règle fixée par la PSSI (politique SSI de l'état) s’applique, notamment :

L'accès hors production nécessite une accréditation / enquête et un poste de travail adapté et maîtrisé par l'administration que l'on puisse raccorder au réseau du MI.

Pour l’accès distant, un poste "bastion" adapté, que l'on appellera ici "poste jaune", sera nécessaire. ( cela s'appelle SPAN aujourd'hui ).

Sur l'environnement de production l'approche est différente et plus contrainte, l'accès à la production est restreint au strict minimum et nécessitera une accréditation renforcée et adaptée et un poste 'rouge' ( niveau habilitation SD ).

Il est recommandé d'anticiper au plus les contraintes en activant rapidement l’environnement de production et de tester le plus tôt les déploiement en production pour que cette partie sujets soit vite maitrisée par les équipes.

Nous réfléchissons à la mise en place d'un "proxy" en lecture seule (au sens une représentation distante) des éléments de vie du système tel que l'état des pipelines et l'observabilité au développeur situé côté primaire ainsi un flux d'échange et de collaboration automatisé, dans la limite où cela n'augmente pas la surface d'attaque.

Des tests de compatibilité avec d’autres solutions d’hébergement d’acteurs du cloud public sont menés, les premiers retours sont concluants.

## Des spécificités à prendre en compte sur la création des conteneurs

Kubernetes impose une rigueur un peu plus élevée à l’initialisation que d’autres solutions.

Les images de conteneurs sont conçues pour s'exécuter “rootless” sur des ports réseaux internes sont > 1024 et ne nécessite pas d'élévation de privilèges.

L’image est minimaliste, concentrée sur une fonction primaire ou atomique du système.

Elles sont conçues pour démarrer très rapidement avec le moins de dépendance possible ( dans l'intérêt de la résilience et du bon fonctionnement de l'orchestrateur)

L’image n'embarque pas de services exposant des services réseau non essentiels à son fonctionnement tel que SSHD.

L’image ne se modifie pas elle-même au lancement. ( ce qui souvent nécessite des élévations de privilèges )

L’écriture dans les pods n’est possible qu’avec le montage d’un volume.

(note : L’exécution du pod bloquée si ces règles ne sont pas respectées ).

cf. <https://docs.openshift.com/>, et en particulier <https://docs.openshift.com/container-platform/4.15/openshift_images/create-images.html> ( toujours vérifier la dernière version )

**Important :**le lancement de pod en ‘root’ est interdit et bloqué au lancement. Ce point n’est pas modifiable. Ceci est un point d’attention majeur, la quasi-totalité des conteneurs à disposition sur les plateformes de partage de conteneurs ne sont pas rootless.

Les pods sont responsables de vérifier au lancement, si l’application est dans la condition initiale de 1er lancement, ou bien s’il faut initialiser ou modifier d’autres ressources telles qu’une base de données.

L’architecture de l’application, hors persistance de données, est conçue pour être complètement stateless, c'est-à-dire, sans aucune persistance de sessions, états et liens, les pods peuvent être basculés à la volée d’un nœud à l’autre sans préavis.

## Des spécificités à prendre en compte sur la topologie réseau et les ouvertures de flux

L’organisation de réseau est segmenté par type de service porté par le flux. ( flux usagers, interdatacenters, interapplicatifs ). Les flux réseau sont ouverts en lecture des manifests kubernetes / helms notamment Ingress et egress.

## Des spécificités à prendre en compte autour de la qualité et de la sécurité des applications

L’objectif d’ensemble est de s’assurer que le code produit est de qualité constante ou accrue, exempt de vulnérabilités algorithmiques ou importées néfastes.

Pour atteindre ces objectifs plusieurs mécanismes doivent être mis en place par l’équipe de développement intégrée :

- minimiser la portion spécifique de code développés en s’appuyant sur le catalogue de service proposé.

- mettre en place une couverture de test unitaire complète du back-end  ( et fournir les moyens de vérification automatisé à la chaîne secondaire )

- mener une analyse de code systématique le plus tôt possible ( les langage et IDE modernes fournissent des fonctions de ce type )

- mener une analyse de CVE des dépendants importées

La chaîne secondaire reconstruit les images à partir des codes sources et procède aux mêmes tests avec des outils complémentaires. L’orchestration du pipeline secondaire est gérée par l’équipe et intègre les tests de vérification issue de la démarche d’homologation de l’application qui fixe les seuils de blocage de déploiement.

Les tests typiques consistent à vérifier la qualité du code ( et la bonne couverture des tests ), et le bon fonctionnement de l’application (non régression) et le scan de vulnérabilité.

L’équipe de développement reçoit via l’interface “shift left” une notification des rapports qui doit être intégrée au flux de travail pour correction.

L’équipe intégrée est invitée à mener une activité constante de refactoring du code produit et du suivi des vulnérabilités de sécurité.La chaîne secondaire est susceptible de bloquer les déploiements si la qualité d’ensemble du code est en baisse ou que le scan fait remonter des Cves critiques. L’équipe est invitée à vérifier et prendre en compte également le résultat des scans de vulnérabilité après la dernière version stable déployée de l'application et de corriger les Cve critiques et importantes.****

**L’équipe prend en compte que si le suivi des plans d’action n’est pas mis en oeuvre et que de surcroît des vulnérabilités critiques sont détectées depuis le dernier déploiement stable,et que l’équipe projet n’a pas pris en compte les injonctions de correction, l’application sera susceptible d’être suspendue jusqu'à la remédiation pour garantir l’intégrité et la protection de ses données**

## Modèle d’intégration d’une application dans le cadre Cloud Native

Le schéma ci-dessous précise le cadre général d’intégration d’une application. Des variantes sont possibles entre les ministères, elles sont précisées directement auprès des équipes concernées. Le respect de cadre permet à la direction d’application d’accéder à un socle de sécurité accélérant les homologations, l’ouverture automatique des segments réseau et l’homologation en continu.

**Vision logique d’ensemble et services de socles et du modèle de sécurité**

![Enter image alt description](images/3eg_Image_3.png)

**Architecture d’intégration réseau et flux typiques**

![Enter image alt description](images/Mm2_Image_4.png)

- (1) Inbound usager : accès à l’application des usagers https / websockets (depuis RIE ou Internet )

- (2a) SSO Citoyens + (2b) SSO AGENT : authentification des usagers ( OIDC / SAML V2 )

- (3) Acces objets S3 : accès à la persistance objets de l’application

- (4) Echanges inter-applicatifs ( bordure externe de l’application) : permet d’échange entre des applications de porteurs différentes, selon plusieurs modalités possibles : API restful synchrone,  Asynchrone , fichiers

- (5a) Autres types de flux : autres types d’échange, sortie vers internet, vers d’autres zone d’hébergement, ou entre des zones de sensibilité différentes

- (5b) Flux d’accès à des services communs ou ressources managées ( de protocoles plus variés)

- (6) échanges entre noeuds de l’application : permet la réplication de l’application entre 2 data centers au même niveau sensibilité de données

- (7a) Déploiement des ressources de l’application : gestionnaire & console DEVSECOPS / le pipeline interagit avec le/les clusters kubernetes et les gestionnaires d’infrastructures utilisés ( ouverture de flux réseaux, etc... )

- (7b) Artefacts images & paramétrage : ensemble des ressources liées à une application ou communes ( ex : sources d’images de référence )

- (7c) Observation : permet de collecter les données liées à l’usage pour la mise au point de l’application ou données de vie.

- (8) Kubernetes, sous la forme d’un ou plusieurs namespace(s) isolés ou couplés : fournis l’espace d’exécution de l’application et la gestion des volumes pour le stockage bloc.

# 4 - Présentation de l’offre interMinistérielle Cloud Pi Native et de ses évolutions pressenties

L’offre Cloud PI native répond aux exigences du CCT à travers un ensemble organisationnel et technique. Elle propose une offre Cloud régalienne, souveraineté, sécurisée et isolée de toute problématique juridique extra-européenne.

La composition de l’offre est amenée à évoluer en termes de catalogue de service selon la demande et les financements disponibles, ces évolutions permettent la diminution de la quantité de code produit par les équipes de développement et l'accélération des performances, typiquement : fonctions as services, services managés, gpu;

Les offres d’hébergement compatibles avec les applications « Cloud Native » du ministère de l’intérieur sont :

- Hébergement de l’application sur les infrastructures internes infogérées ;

- Hébergement de l’application sur des infrastructures cloud externes ;

- Hébergement de l’application sur des infrastructures gérées par l’application.

L’ensemble de l’administration technique de la plateforme et des infrastructures est automatisée, pilotée par le développeur/concepteur via l’orchestration DevSecOps avec mise en œuvre d’un principe dit *gitops*: la plateforme de production “tire” le déploiement.

Pour rappel, le développeur n’accède pas directement à l’environnement de production. Toute correction ou évolution suit le processus de déploiement automatisé passe via le principe “gitops” évoqué ci-dessus. Le développeur dispose d’un accès libre à ses environnements (via un poste bastion si l’environnement est situé côté ministériel) il dispose également d’un accès proxifié aux indicateurs de la production. La service team qui l’accompagne, avec les accréditations nécessaires, dispose quant à elle d’un poste dédié lui permettant d’accéder directement via un bastion aux services d’observabilité et faciliter le débogage en production. (note modalité en cours d’évaluation incrémentale )

L’ensemble du code source de l’offre Cloud PI Native et sa documentation sont disponibles sur demande en open-source sous la licence Apache2. Toute contribution est bienvenue.

La politique de segmentation d’hébergement est présentée ci-dessous :

![Enter image alt description](images/b5p_Image_5.png)

Note : chaque région est autonome dans son fonctionnement. Seul le service de stockage objet de type S3 est accessible sur l’ensemble des régions ministérielles. ( réplication en proximité dans le datacenter).

### Les magasins de composants kubernetes et d’image de base

Associée avec l’offre Cloud pi Native, des magasins de composants Kubenetes sont mis à disposition incrémentalement selon les besoins des applications cela inclut celui de l’éditeur RedHat. Le développeur peut dès aujourd’hui s’appuyer sur un catalogue porté par l’Insee autour de son produit Onyxia : [https://github.com/InseeFrLab/helm-charts](https://github.com/InseeFrLab/helm-charts)

L’équipe produit est fortement invitée à l’utiliser ces composants courants et ne pas refabriquer une version dédiée dont le cycle ne sera pas en adéquation avec les besoins de réactivité en mcs.

A propos des images de base nues, il est recommandé d’utiliser les versions dites "LTS" , certifiées et maintenues selon un processus qualité au sein des communautés ou éditeurs pour la construction des pods/conteneurs. Debian, Redhat, Ubuntu font partie des communautés les plus attentives.

Sur les besoins "classiques" de persistance : postgres, redis, mariadb, mongodb, elastic, etc… l’approche recommandée de s’appuyer sur les opérateurs kubernetes disponibles et les objets statefullSet. Sur le cluster de production les opérateurs sont déployés par l’hébergeur car généralement ils requièrent les droits globaux.

L’équipe projet doit vérifier les versions disponibles lors de la conception de son projet.

# 6 - Introduction à l’offre de service du ministère (Béta)

![Enter image alt description](images/offre-clou-pi-native-220424.png)

[Lien pour demander l'établissement d'une convention](https://www.demarches-simplifiees.fr/commencer/cloud-pi-native)

[Lien pour accéder à un schéma d'architecture de référence (cf. ci-après)](<https://app.diagrams.net/?url=https%3A%2F%2Fraw.githubusercontent.com%2Fcloud-pi-native%2Fcct-cloud-native%2Fmain%2FDAG-exemple.drawio>)

![Enter image alt description](images/DAG-exemple.drawio.png)


- [Lien vers l'annexe présentant les normes applicables](./cct-normes.md)
- [Lien vers la liste des exigences associées au CCT](./cct-exigences.md)
- [Lien vers le glossaire](./cct-glossaire.md)
