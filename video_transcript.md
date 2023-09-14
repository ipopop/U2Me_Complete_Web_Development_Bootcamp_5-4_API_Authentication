### Transcription vidéo :

```
Dans cette leçon, nous allons apprendre tout ce qu'il faut savoir sur l'authentification et l'autorisation des API, c'est-à-dire

la capacité de prouver que vous avez les droits d'accéder à une API particulière.

Précédemment, nous avons vu que nous étions capables de faire des requêtes très simples en utilisant Axios ou en venant de notre

côté serveur et aussi en le faisant via Postman.

Mais vous pouvez imaginer qu'il existe de nombreux scénarios dans lesquels vous ne souhaitez pas que tout le

monde puisse accéder à votre API.

Disons que les données que vous conservez derrière votre API sont une ressource, n'est-ce pas ?

Considérons-les comme de l'argent car, après tout, à notre époque, les données sont extrêmement précieuses.

Dans ce cas, imaginons que nos données soient enfermées dans un coffre-fort, comme dans une banque, et que notre API

soit le guichet où nous pouvons recevoir et traiter les demandes de nos clients.

Supposons que quelqu'un de mal intentionné se présente et dise : "J'aimerais obtenir 100 livres sterling en utilisant l'API",

et qu'il essaie de s'approprier une ressource.

Jusqu'à présent, cela fonctionne avec tout ce que nous avons vu.

Notre API disait : "Eh bien, voilà, voici l'argent que vous avez demandé et il s'en va".

Ce que nous voulons, c'est que dans certains scénarios, nous puissions protéger les ressources derrière notre

API en utilisant l'authentification.

Comment cela fonctionne-t-il ?

Dans ce cas, nous devons savoir qui vous êtes lorsque vous faites ces demandes.

Et selon que l'on dispose ou non de l'authentification, on peut dire, oh 401 non autorisé.

Désolé, vous ne pouvez pas faire cela.

Dans cette leçon, nous allons apprendre exactement comment nous pouvons authentifier l'utilisateur ou le client

qui fait la demande d'API et, selon qu'il est autorisé ou non à faire cette demande, nous pouvons

lui envoyer les données ou lui dire non, désolé, ce n'est pas autorisé.

En termes d'authentification, j'aime à penser qu'il y a quatre niveaux.

Il y a l'authentification zéro, donc aucune.

Et c'est avec cela que nous avons travaillé jusqu'à présent.

Il y a l'authentification de base, l'API, l'autorisation basée sur une clé et l'authentification basée sur un jeton.

Je vous expliquerai un peu plus loin quelle est la différence entre l'authentification et l'autorisation.

Commençons par l'ordre de sécurité et par le premier type, à savoir l'absence d'authentification.

Nous avons déjà vu des API sans authentification.

Par exemple, lorsque nous avons travaillé avec l'API du conseil d'administration, aucun des points d'extrémité de l'API ne nécessitait

d'authentification.

Que peut donc faire une API pour éviter les abus ?

Supposons que quelqu'un fasse beaucoup trop de demandes et qu'il n'y ait aucun moyen de vérifier qui il est

ou d'où il vient.

Les fournisseurs d'API peuvent alors ajouter un contrôle de sécurité en fixant une limite de taux.

Comme vous l'avez vu dans l'instance API du conseil, nous avons fixé une limite de 100 requêtes par 15 minutes. J'ai fixé cette limite de manière à ce que, dans la plupart des

cas, en tant qu'étudiant, cela soit suffisant pour que vous puissiez travailler avec l'API, obtenir

les données et essayer les choses que vous voulez essayer, sans que cela n'entraîne une surcharge de travail et que l'API

ne devienne inutilisable pour tout le monde.

C'est donc une façon de procéder.

Vous pouvez donc vérifier pour chaque adresse IP le nombre de requêtes qu'elle effectue par minute et, sur la base d'une décision

arbitraire, vous pouvez dire : "Je vais limiter le nombre de requêtes à ce chiffre".

C'est donc quelque chose que l'on voit souvent avec les API publiques qui n'ont pas d'authentification, et l'absence d'authentification est excellente parce

qu'elle signifie qu'elle est super inclusive.

Tout le monde peut l'utiliser.

Il est très facile de démarrer et, en général, si vous n'avez pas de données changeantes à protéger ou de données qui doivent

être attribuées à un utilisateur particulier, vous ne voyez très souvent pas d'API d'authentification.

Si vous consultez la documentation de l'API du conseil d'administration, vous verrez que tous les points de terminaison ne nécessitent

aucune authentification et que vous pouvez simplement faire la demande comme n'importe qui et obtenir les données

en retour.

Mais les demandes d'API sont en fait limitées en termes de taux, ce qui signifie que nous disposons de certaines mesures de sécurité, bien

qu'il ne s'agisse pas d'une mesure d'authentification ou d'autorisation de tout type d'utilisateur d'API.

Passons au niveau de sécurité suivant, l'authentification de base.

Et comme son nom l'indique, il est assez basique.

Comment cela fonctionne-t-il ?

Vous fournissez un nom d'utilisateur et un mot de passe lorsque vous faites une demande d'API.

Ce que cela signifie.

Vous vous authentifiez auprès du fournisseur d'API.

Vous avez un compte auprès du fournisseur d'API.

En fournissant ces deux informations, vous prouvez votre identité.

En général, l'authentification de base se fait en transmettant une chaîne codée en base 64 dans l'en-tête

de la requête.

Qu'est-ce que l'encodage base64 ?

En fait, il s'agit de prendre du texte en Ascii.

Tout ce que vous pouvez taper sur votre clavier et qui peut être converti en bits.

Donc des zéros et des uns pour représenter ce caractère particulier.

Ensuite, nous pouvons prendre les bits et les encoder dans un autre caractère.

En général, lorsque nous effectuons un encodage base64, il y a un peu d'expansion.

Ainsi, par exemple, en commençant par le mot man m a n, le résultat final que nous obtenons après avoir effectué

notre encodage base64 est t w f u et vous pouvez voir que nous avons un caractère de plus qu'auparavant.

Et selon que vous avez des espaces dans votre ligne d'encodage source, vous pouvez également voir des caractères

supplémentaires.

Chaque caractère est représenté en binaire, et j'ai vu des personnes capables de lire le binaire, ce qui est une compétence extraordinaire, mais

qui n'est probablement pas très utile car les ordinateurs peuvent le faire plus rapidement.

Après tout, il s'agit d'un langage informatique, n'est-ce pas ?

Lorsque nous avons commencé à utiliser des ordinateurs, nous avions un bouton pour allumer et un bouton pour éteindre.

Et en allumant et éteignant les choses, nous pouvions représenter à l'ordinateur

ce que nous voulions taper ou ce que nous voulions qu'il calcule et fasse tous les calculs et toutes les choses que les ordinateurs

font par le biais de ces zéros et de ces uns ou de ces allumages et de ces extinctions.

Comme vous pouvez le constater, chaque caractère auquel vous pouvez penser est représenté en binaire.

En prenant ce binaire et en le faisant passer par une méthode d'encodage spéciale, nous obtenons base64 et

nous le formatons simplement dans ce format.

Donc le nom d'utilisateur et le mot de passe.

Et nous convertissons tout cela en base 64.

Vous obtiendrez donc une sorte de longue chaîne de caractères représentant ces données.

Mais en base 64.

Vous pouvez ensuite l'ajouter à un en-tête d'autorisation et transmettre ces données lors

de vos requêtes.

Voyons comment cela fonctionne en pratique en l'essayant avec Postman.

L'API que nous allons utiliser est une autre de nos propres API, appelée API Secrets.

Cette API a donc pour but de mettre vos confessions dans une base de données et de permettre aux gens de partager et de voir les

secrets des autres de manière anonyme.

L'API comporte différents points de terminaison avec différents niveaux d'authentification.

Cette API nous permet d'enregistrer un nouvel utilisateur en lui transmettant un nom d'utilisateur et un mot de passe dans le

corps de la demande d'envoi.

Une fois que nous nous sommes enregistrés sur le service, nous pouvons utiliser ce nom d'utilisateur et ce mot de passe pour effectuer une

requête en utilisant l'authentification de base.

Le fonctionnement de nos points d'extrémité sur cette API de repos est le suivant : si vous voulez obtenir un secret aléatoire de la base de

données des secrets, vous n'avez pas besoin de vous authentifier parce que nous envoyons un petit morceau de

données.

Les gens ne vont probablement pas emprunter cet itinéraire très souvent, mais

si vous voulez quelque chose d'un peu plus impliqué, d'un peu plus grand en termes de taille de la réponse et aussi d'un peu plus

précieux en termes de nos ressources, alors nous avons une porte.

Nous utilisons donc l'authentification de base pour nous assurer que vous êtes au moins un utilisateur enregistré.

Et si, par la suite, nous voulons nous assurer que nous vérifions quels sont les utilisateurs qui font beaucoup de demandes.

Vous voulez donc avoir un niveau payant pour votre API, tout cela est possible.

Faisons donc une demande à ce point de terminaison en utilisant l'authentification de base et Postman.

J'ai donc Postman ici à droite et je fais une requête Http get et l'URL que je vais atteindre

est cette URL particulière.

Il s'agit de l'URL de base pour notre secret API stash api. com et je vous encourage à lire la documentation comme toujours

avant de faire une quelconque requête à une API.

Cette API possède un paramètre de requête appelé page, car lorsque vous obtenez tous les éléments de données, par exemple tous les secrets de la base

de données, cela va représenter beaucoup de données et nous ne voulons pas envoyer des quantités

massives de données sur Internet lorsque les gens font des demandes d'API.

Normalement, les fournisseurs d'API peuvent paginer la réponse, c'est-à-dire qu'ils vous donnent

dix ou vingt pages à la fois et vous pouvez demander la page que vous voulez, par exemple la page

1.

Une fois que vous avez traité les données, vous pouvez demander la page 2 et ainsi de suite.

Il s'agit simplement d'un des paramètres que nous pouvons ajouter au paramètre de requête pour déterminer le type de réponse

que nous obtenons.

Ce qui importe maintenant, c'est l'autorisation ou l'authentification.

Le type d'authentification que nous voulons utiliser est l'authentification de base.

Nous devons saisir un nom d'utilisateur et un mot de passe pour que cela fonctionne.

Ce que je veux que vous fassiez est d'aller de l'avant et d'utiliser ce post slash register pour vous enregistrer un nom d'utilisateur

et un mot de passe et une fois que c'est fait, allez de l'avant et utilisez ce nom d'utilisateur et ce mot de passe pour accéder

au forward slash ou à la route.

Mettez la vidéo en pause ici et essayez.

D'accord.

Voyons donc cela en détail.

La première étape consiste à envoyer une demande de courrier à la voie d'enregistrement.

Allons-y et accédons au bon point de terminaison, puis passons des paramètres de corps au format

de formulaire encodé en URL.

Nous avons deux clés, un nom d'utilisateur et un mot de passe.

Et je vais mettre un utilisateur au hasard, disons notre utilisateur Jack Bauer.

Imaginons que Jack Bauer veuille utiliser notre API et confesser certains de ses secrets les plus profonds et les plus sombres.

Je vais donc taper un mot de passe, puis je vais cliquer sur "envoyer" pour faire cette demande.

J'espère que vous verrez dans les réponses que nous obtenons un statut 200, ce qui signifie

que tout s'est bien passé et que je suis maintenant enregistré avec succès.

Gardez votre nom d'utilisateur et votre mot de passe car nous allons en avoir besoin dans notre

authentification de base pour essayer de demander tous les secrets que nous avons, notre type d'autorisation sélectionné comme

authentification de base, et ensuite je vais taper mon nom d'utilisateur et mon mot de passe.

Une fois que j'ai obtenu ces deux données, je clique sur "envoyer" et vous verrez que nos secrets nous

reviennent à raison de dix par page.

Je tiens à préciser que lorsque nous utilisons l'authentification de base avec Postman, ce dernier effectue des opérations

magiques dans les coulisses.

Pour nous, il s'agit de générer automatiquement l'en-tête d'autorisation sur la base du nom d'utilisateur

et du mot de passe que vous avez fournis ici.

Vous pouvez voir ceci si vous allez dans l'onglet des en-têtes et vous pouvez voir

qu'ils ont automatiquement généré cet en-tête avec une clé d'autorisation et une valeur de base avec le B en majuscules et ensuite une chaîne qui représente votre

nom d'utilisateur et votre mot de passe.

Je peux vous le prouver en copiant votre propre chaîne de caractères générée par

Postman et en allant sur un site Web appelé Base64 D code. org et collez cette chaîne dans la boîte du haut, cliquez sur Décoder

et vous pouvez voir qu'elle est automatiquement décodée dans le format original, qui est nom d'utilisateur deux fois le mot

de passe.

Et c'est essentiellement ce qui se passe en coulisses.

Ainsi, lorsque vous effectuez des requêtes côté serveur qui nécessitent une authentification ou une autorisation de base, vous pouvez également

le faire vous-même.

Créez les en-têtes, utilisez ceci comme une chaîne, convertissez votre nom d'utilisateur et votre mot de passe, ajoutez le mot basic

et ajoutez ceci comme en-tête.

Mais dans la plupart des cas, si vous utilisez une bibliothèque comme Axios, elle pourra générer tout cela pour vous en fournissant

votre nom d'utilisateur et votre mot de passe.

D'accord.

Avez-vous réussi à faire fonctionner ce système ?

Avez-vous réussi à utiliser l'authentification de base pour vous authentifier auprès du fournisseur d'API

et obtenir quelques secrets ?

Comme si je parlais à mon poisson de compagnie et que j'imaginais qu'il me répondait par des répliques pleines d'esprit.

Ah, nous sommes tous passés par là.

Nous venons de voir l'absence d'authentification et l'authentification de base en action en ce qui concerne les API.

Passons maintenant à l'autorisation de la clé API.

Une chose que vous remarquerez, c'est que le terme autorisation, si vous êtes aux États-Unis, s'écrit

avec un Z, mais je suis au Royaume-Uni, donc il s'écrit avec un S autorisation par opposition à authentification.

Quelle est la différence ?

Parce qu'on l'entend souvent et qu'on se demande souvent si on utilise l'autorisation ou l'authentification.

La différence entre ces deux formulaires est donc que si vous avez un utilisateur, il peut s'authentifier auprès de

votre service.

Cela signifie que vous vous connectez ou que vous vous inscrivez.

Mais l'autorisation est simplement un client qui est autorisé à utiliser votre service avec une clé API qui peut être associée à un

utilisateur, auquel cas il s'authentifie et obtient ensuite une clé API pour

s'autoriser à utiliser votre API.

Mais il se peut que vous n'ayez même pas besoin de vous enregistrer auprès du fournisseur d'API et

que vous puissiez simplement obtenir une clé d'API et vous autoriser auprès du fournisseur d'API.

C'est là toute la différence.

L'autorisation est quelque chose qui vous permet d'utiliser une API.

L'authentification est un élément qui vous permet d'être identifié en tant qu'utilisateur par le fournisseur d'API.

Vous constaterez que de nombreuses API publiques utilisent des clés d'API, ce qui est très utile car vous pouvez alors suivre

l'utilisation par clé d'API.

Par exemple, si vous vous êtes inscrit à l'API Google Maps, vous pouvez utiliser toutes sortes d'API

différentes, par exemple l'API places pour trouver toutes les choses qui apparaissent sur Google

Maps.

Vous pouvez également utiliser la matrice de distance pour calculer la distance entre deux points dans le temps, toujours

à l'aide des API de Google.

Et chaque fois que vous faites une demande, vous devez utiliser cette clé avant de pouvoir obtenir une réponse, puis

ils peuvent enregistrer Eh bien, combien de demandes faites-vous avec cette clé ?

Vous pouvez donc voir que, dans ce cas, l'API des lieux est utilisée 200 000 fois par jour.

Vous faites donc 200 000 demandes par jour.

Et comme pour la plupart des API publiques, ils doivent mettre en place leur propre infrastructure, leurs propres serveurs, ils doivent

assurer la maintenance de ces ordinateurs serveurs, etc.

Les coûts sont importants et il est donc fréquent qu'ils vous fassent payer l'utilisation de leurs API.

Par exemple, dans le cas présent, cette personne accumule 2 000 dollars d'utilisation de l'API et, en examinant la fréquence à laquelle vous devez

effectuer des requêtes via votre clé API, elle peut déterminer le montant qu'elle doit vous facturer.

Il est utile de savoir cela à la fois en tant qu'utilisateur et fournisseur d'API. Dans les prochaines leçons, nous verrons comment

créer nos propres API et nous examinerons l'autre côté de la médaille.

Mais pour l'instant, concentrons-nous sur le côté client.

Pour l'instant, si vous vous reportez à la documentation de l'API Secrets, vous verrez

que certains points de terminaison nécessitent une API pour autoriser votre utilisation et pour obtenir une API, il y a le point de

terminaison de génération de clé API, que nous avons gardé assez simple pour l'instant.

Cela vous permet d'accéder à cette route, de faire une requête et d'obtenir votre propre clé API à utiliser.

Une fois que vous avez généré la clé API, vous pouvez faire défiler l'écran jusqu'au point de terminaison du filtre.

Ce point de terminaison vous permet de renvoyer certains secrets avec un score d'embarras particulier. Vous verrez

donc que chacun des secrets est associé à des scores d'embarras ou au score M.

Il s'agit simplement d'un moyen pour l'utilisateur de fournir un élément de métadonnées.

Sur une échelle de 1 à 10, quel est le degré d'embarras de votre secret ?

En utilisant ce point final de filtrage, nous pouvons fournir ce score comme paramètre de requête et ensuite nous pouvons fournir

un nombre pour dire quel est le score minimum d'embarras à filtrer ?

Mais surtout, pour que cette requête soit acceptée, nous devons également transmettre la clé de l'API en tant que paramètre

de requête.

Il s'agit de la clé que nous avons générée précédemment à l'étape générer une clé API.

Je vous invite donc à mettre la vidéo en pause et à faire un essai à l'aide de l'outil.

Documentation de Secret Stash AP, Africom vous propose d'utiliser Postman pour mettre la main sur tous les secrets

embarrassants qui ont un score d'embarras de sept ou plus.

Mettez donc la vidéo en pause.

Essayez-le.

D'accord.

La première étape consiste donc à générer une clé.

Nous nous rendions donc sur le site web.

Peut-être devrons-nous donner les détails de notre carte, peut-être devrons-nous nous inscrire et nous connecter.

Mais quoi qu'il en soit, à un moment donné, nous utiliserons ce point de terminaison et demanderons à l'API de nous donner une clé d'accès.

Une fois que nous avons obtenu la clé d'accès, nous pouvons aller chercher les itinéraires qui en ont besoin dans l'API

Secrets.

Il s'agit du point final du filtre.

Nous pouvons adresser nos demandes à ce point d'accès.

Forward slash filter et nous pouvons ajouter le paramètre appelé score qui indique à l'API quel est le score minimum.

Nous voulons filtrer par et je règle cela sur sept.

En ce qui concerne l'autorisation, nous pouvons fournir notre clé API ici, où nous disons ce qu'est la clé et ce qu'est

la valeur.

La clé ici est la clé API, épelée avec un K majuscule, comme vous pouvez le voir dans les documents et notre valeur, je vais juste la coller

à partir de l'endroit où nous l'avons obtenue et nous allons l'ajouter aux paramètres de la requête avec les

clés API.

Parfois, l'API vous demande de l'ajouter à l'en-tête de la requête et d'autres fois, elle vous

demande de l'ajouter au paramètre de la requête.

Cela dépend de l'API et vous devriez toujours lire leur documentation pour comprendre ce que vous devez faire.

Nous sommes maintenant prêts à envoyer le message.

Une fois que vous avez fait cela, si vous avez une clé correcte, vous devriez obtenir

des secrets qui sont tous filtrés par le score M.

Voyons voir, quels sont certains de ces secrets embarrassants ?

J'ai une collection secrète de photos d'enfance embarrassantes que j'utilise pour faire chanter mes frères et sœurs.

Un frère plutôt utile, un maître chanteur.

Très bien, examinons maintenant la dernière forme d'authentification que nous souhaitons aborder, à savoir

l'authentification par jeton.

Pourquoi les niveaux de sécurité augmentent-ils ?

L'authentification de base utilise un nom d'utilisateur et un mot de passe qui sont transmis sous la

forme d'une chaîne encodée en base64 dans l'en-tête.

Comme vous l'avez vu, j'ai pu facilement utiliser le décodeur base64 pour récupérer en clair le nom d'utilisateur et

le mot de passe.

Cela signifie qu'il est tout aussi possible pour quelqu'un sur l'internet d'intercepter vos demandes d'API

et de faire la même chose.

Alors pourquoi l'utilise-t-on encore ?

La plupart des fournisseurs d'API qui utilisent l'authentification de base ont Https sur leur domaine, ce qui signifie que nous utilisons la

cryptographie pour coder de manière sécurisée toutes les données qui sont transmises dans les deux sens.

Et même si quelqu'un intercepte les paquets, il ne verra pas la chaîne telle que nous l'avons vue.

Au lieu de cela, il s'agira d'un charabia qu'ils ne pourront pas décoder.

Il n'en reste pas moins que le nom d'utilisateur et le mot de passe sont transmis.

Et s'il s'agit d'un site web moins sûr ou si quelque chose ne fonctionne pas, il y a un risque.

L'autorisation par clé API est un peu plus sûre, car nous ne saisissons nulle part notre nom d'utilisateur et notre

mot de passe.

Au lieu de cela, nous avons cette clé API qui peut être supprimée et régénérée.

Il peut être assorti de plafonds, ce qui permet de limiter le taux.

Vous pouvez dire que je génère cette clé, mais que je ne veux faire que mille demandes par mois, par exemple, et que

je ne paie donc que pour ce montant.

Ainsi, même si quelqu'un intercepte cette clé API, il ne pourra pas s'emparer du nom d'utilisateur et du mot de passe.

Ils ne disposeront d'aucune de vos données de paiement.

Il s'agit simplement d'un code réutilisable que vous utilisez pour accéder à une API.

Enfin, l'autorisation ou l'authentification basée sur un jeton est encore plus sûre, car nous demandons

à l'utilisateur d'utiliser un nom d'utilisateur et un mot de passe pour se connecter et, une fois qu'il s'est connecté, nous générons un jeton à utiliser

avec l'API, de sorte que l'API ne s'occupe pas du nom d'utilisateur et du mot de passe, mais que c'est le jeton qui est constamment

utilisé pour interagir avec l'API.

Normalement, l'authentification basée sur un jeton est appelée OAuth et OAuth 2. 0 est probablement la norme industrielle pour

l'authentification par jeton.

C'est un peu ce qui se passe en coulisses.

Vous avez un utilisateur pour un service et vous voulez être en mesure d'agir en son nom. Vous lui demandez donc de se connecter avec son nom d'utilisateur

et son mot de passe sur le site web du fournisseur de l'API, puis...

Le fournisseur d'API génère un jeton à partir de ce jeton.

Ce jeton peut ensuite vous être transmis en tant que tiers et vous pouvez l'utiliser pour interagir

avec l'API.

Prenons un exemple concret.

Supposons que vous construisiez une application tierce, disons une application météo, mais que vous ayez une particularité

dans l'application : vous allez vous emparer des événements d'un utilisateur dans son calendrier Google.

Vous voulez donc voir qu'ils ont une réunion, par exemple, le mardi et qu'elle a lieu à Baltimore.

Vous récupérez donc tous ces éléments de données et vous regardez le temps qu'il fait à cet endroit et à cette date,

et vous pouvez peut-être envoyer une alerte à l'utilisateur pour lui dire d'apporter un parapluie à l'événement

en question.

C'est l'idée derrière l'interaction avec les API de Google Agenda pour que l'utilisateur puisse vous accorder

l'accès à ces données.

Si vous n'utilisez pas l'authentification par jeton, vous devez

nous fournir le nom d'utilisateur et le mot de passe de ce tiers, afin que nous puissions l'utiliser pour interagir avec l'API de

l'agenda Google.

Au lieu de cela, nous pouvons utiliser l'authentification basée sur un jeton ou OAuth pour que

l'utilisateur se connecte à Google, ce qui génère un jeton que nous pouvons utiliser pour interagir avec l'API

Google Calendar et ainsi obtenir les événements et les réunions de l'utilisateur.

Nous pouvons même enregistrer ou supprimer des données.

Nous pouvons interagir avec l'agenda Google en tant qu'utilisateur sans avoir besoin de connaître son nom d'utilisateur

et son mot de passe.

Au lieu de cela, toutes les questions de sécurité sont gérées par Google.

Il s'agit donc d'un moyen beaucoup plus sûr de procéder à l'authentification de l'API.

Chaque fois que vous avez vu cet écran vous demandant d'autoriser une application particulière

au nom de votre compte Google, vous avez effectué cette opération.

Mais voyons cela plus concrètement en utilisant notre API.

Si vous jetez un coup d'œil à l'API Secrets, vous verrez qu'il existe un chemin qui nous permet

d'obtenir des secrets sur la base de l'ID du secret.

Ce chemin est protégé par l'authentification par jeton porteur et l'authentification par jeton porteur utilise le nom d'utilisateur

et le mot de passe d'un utilisateur pour s'authentifier sur notre serveur, puis notre serveur génère un jeton qui sera utilisé

comme proxy pour que toute autre personne puisse interagir avec l'API en tant qu'utilisateur, nous pouvons utiliser le chemin get auth token

en envoyant une requête avec un corps de nom d'utilisateur et de mot de passe.

Une fois que le serveur a réussi à authentifier l'utilisateur, il lui renvoie un jeton que nous

pouvons utiliser pour interagir avec le reste de l'API.

Vous le verrez très souvent lorsque vous voudrez poster quelque chose au nom d'un utilisateur ou modifier ou

supprimer quelque chose au nom d'un utilisateur, vous interagirez avec un service comme si vous étiez l'utilisateur.

Mais comme nous utilisons l'authentification par jeton, vous n'avez jamais besoin de connaître leur nom d'utilisateur

et leur mot de passe et nous pouvons garder tout cela en sécurité.

Tentons l'expérience.

Ouvrez postman et voyez si vous pouvez trouver comment obtenir les secrets en utilisant ce point de terminaison

et obtenir le secret avec un ID de deux.

Mettre la vidéo en pause.

Essayez-le.

D'accord.

Nous devons d'abord utiliser ce chemin d'accès au jeton d'authentification pour obtenir un jeton d'authentification et nous allons faire une

requête post à ce chemin d'accès.

Changeons donc cela.

Et nous voulons ajouter dans le corps une forme de données codées en URL et nous voulons lui transmettre notre nom d'utilisateur

et notre mot de passe.

J'utilise le nom d'utilisateur et le mot de passe que j'ai obtenus lors de mon inscription

et je transmets les valeurs.

Ensuite, je vais aller de l'avant et appuyer sur le bouton "Envoyer".

Si vous le faites pour la première fois, vous verrez que votre jeton est généré.

Si vous faites cela pour la deuxième fois, vous obtenez toujours le même jeton.

Mais il vous dit que vous avez déjà reçu un jeton et vous rappelle simplement de quoi il s'agit.

Les deux options peuvent se produire, mais une fois que nous avons obtenu notre jeton, nous pouvons l'utiliser pour obtenir un

secret avec un identifiant particulier.

Copions le point final et modifions ce paramètre URL pour obtenir le secret avec

un ID de deux.

Maintenant, avant de pouvoir l'envoyer, je dois changer l'autorisation en autorisation

de jeton porteur et je vais coller le jeton que j'ai reçu à l'étape précédente ici.

Comme pour l'authentification de base, Postman génère un en-tête d'autorisation

en coulisses.

Automne statiquement basé sur le jeton que vous mettez ici.

Et vous pouvez le voir en allant dans les en-têtes, vous pouvez voir qu'il a généré

un en-tête avec la clé d'autorisation et la valeur de porteur, et ensuite le jeton que vous avez ajouté ici.

Si vous le faites vous-même en utilisant un simple code, il s'agit de la valeur complète de l'en-tête que

vous envoyez avec votre requête.

Si tout a fonctionné, nous recevrons en retour le secret avec un

identifiant de deux.

Il est maintenant temps de faire un exercice et de refaire tout ce que nous venons de faire, en explorant les différentes

façons de s'authentifier ou de s'autoriser avec une API.

Mais cette fois-ci, nous allons le faire avec du code.

Allez-y et téléchargez les fichiers de départ 5. 4 API auth zip extraire le zip et l'ouvrir dans vs code.

Une fois que vous êtes ici, la première chose que je veux que vous fassiez est de CD vers le dossier API authentication et ensuite je veux que

vous fassiez votre truc habituel où vous utilisez NPM pour installer tous les modules node nécessaires.

Ensuite, je veux que vous alliez à solution dot JS sans défiler vers le bas, sans regarder la solution.

Je vais mettre à jour toutes ces constantes en utilisant votre nom d'utilisateur, votre mot de passe, votre clé API, votre jeton de

porteur que vous avez généré plus tôt lorsque nous avons parcouru chacune des étapes de Postman.

Une fois que vous avez fait cela, je veux que vous utilisiez Nodemon pour exécuter la solution dot js et ensuite nous pouvons nous

rendre sur localhost 3000 et vous verrez ce site web de base.

Nous pouvons maintenant cliquer sur chacun de ces boutons d'authentification.

L'absence d'authentification nous donne un secret aléatoire, l'authentification de base.

Nous nous rendrons sur le chemin de l'accès à tous.

L'authentification par clé API nous donnera le point de terminaison filtré et l'authentification par jeton porteur nous donnera un secret avec un identifiant

particulier. Vous pouvez donc voir que nous utilisons tous les mêmes points de terminaison que nous avons utilisés avec Postman,

mais cette fois-ci nous l'utilisons à partir de notre serveur, donc nous faisons des requêtes côté serveur en utilisant

Axios, mais nous nous assurons également que nous apprenons à le faire en utilisant tous les différents types d'authentification.

Jetez un coup d'œil à l'index. Il se peut que vous ayez besoin de vous rappeler comment

faire des demandes en utilisant Axios et que vous ayez besoin d'utiliser certains des conseils

qui sont disponibles dans chacune des étapes.

Mais pour l'essentiel, vous devriez être en mesure de compléter ce code côté serveur de manière à ce qu'il fonctionne de la même manière que la

solution.

Dot js.

Mettez la vidéo en pause et essayez.

D'accord.

Comment cela s'est-il passé ?

Examinons le code de la solution et voyons si vous avez réussi à la faire fonctionner.

La première étape consiste à remplir toutes les valeurs que vous avez obtenues à partir des trois différents types d'authentification.

Une fois que vous avez fait cela, nous allons utiliser chacune de ces constantes dans les différents types d'authentification.

Le premier que nous allons faire est donc la route qui n'a pas d'authentification.

Nous utilisons donc un bloc try catch et nous utilisons Axios pour faire une requête get à l'URL de notre API au point de terminaison

aléatoire.

C'est assez simple.

Une fois que nous avons récupéré les données, nous les transmettons à l'index. js et nous utilisons Json Stringify pour le transmettre comme une

simple chaîne de caractères au lieu d'un objet JavaScript.

Ce contenu est ensuite repris dans l'index. js et affichés dans cette boîte ici.

Il s'agit simplement de nous mettre en appétit et de nous faire démarrer.

La prochaine utilise l'authentification de base et si vous ne savez pas comment faire, comme toujours,

Google est votre ami.

Mais mieux encore que Google, c'est moi qui suis votre ami, car j'ai fourni cet indice pour vous montrer comment vous auriez

pu chercher cette question particulière de StackOverflow, à savoir comment envoyer l'authentification

de base avec Axios ?

C'est à peu près ce que nous voulons faire ici.

C'est vrai ?

Il nous indique qu'il existe un paramètre auth que nous pouvons ajouter à nos requêtes en ajoutant un nom d'utilisateur

et un mot de passe.

Ce que nous pouvons faire, c'est fournir cette authentification après avoir fourni le point de terminaison et nous pouvons ajouter notre nom d'utilisateur ou

notre mot de passe sous ce nom de paramètre d'authentification et cela fera tout l'encodage base64 pour nous et ensuite nous pouvons

envoyer cette requête et nous devrions être en mesure de récupérer nos données, que nous transformons à nouveau en

une chaîne et que nous envoyons à l'interface.

La prochaine étape consiste à utiliser la clé API.

N'oubliez pas que, dans notre cas, la clé API est également envoyée en tant que paramètre.

Avec Axios, nous pouvons envoyer des paramètres comme suit.

Nous pouvons également les ajouter à la fin de notre URL.

Les deux méthodes sont correctes.

Cela dépend vraiment de celui que vous voulez utiliser.

Et si vous avez cherché ou regardé les stocks axiaux, vous verrez peut-être quelque chose comme ça, mais vous verrez aussi

que d'autres personnes l'ajoutent directement dans le point final.

Peu importe la méthode utilisée, pourvu qu'elle soit efficace.

Nous avons dû fournir un paramètre sous la forme d'un score.

Le score d'embarras sur lequel nous voulons filtrer et notre clé API.

Une fois que nous avons récupéré les données, nous les transmettons au front-end.

La dernière nécessite un jeton de porteur.

Dans ce cas, nous accédons au point de terminaison secrets et nous fournissons l'ID de deux pour obtenir

ce secret particulier.

Je passe maintenant la configuration afin de pouvoir fournir un paramètre pour le paramètre headers.

Je mets ici l'autorisation comme clé et la valeur comme le mot bearer avec un B majuscule, un espace,

puis le bearer token que nous avons généré plus tôt.

Encore une fois, j'ai ajouté un indice pour vous aider à comprendre, mais il s'agit essentiellement de la configuration et vous pouvez soit

ajouter cet objet directement ici, comme nous l'avons fait avec nos paramètres ou avec notre authentification, ou vous pouvez

le séparer de la manière que vous préférez.

Ensuite, nous envoyons une requête "get", nous récupérons les données et nous les envoyons au front-end.
```