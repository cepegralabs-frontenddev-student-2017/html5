# css
## Cascading Stylesheets

### Préambule

Nous avons vu ensemble l’HTML4 en premier lieu.
Maintenant, avec les feuilles de styles, nous allons séparer le contenu de sa mise en forme.
C’est très pratique et les feuilles de styles vont vous ouvrir des portes au niveau de la mise en forme que vous n’auriez même pas pu imaginer en restant enfermés dans les règles strictes du vieux HTML4.
Nous commencerons par une approche des CSS dans leur version 2.0 car elle a servi de base pour la version suivante. Nous embrayerons ensuite rapidement vers les CSS dans leur version 3.0 qui est toujours en cours de développement.
À ce stade-ci il est important de se rappeler une chose : toutes les règles que nous allons utiliser ici ne sont pas forcément interprétées de la même façon d’un navigateur à l’autre. Une vérification régulière est donc fortement conseillée.

### table des matièrestant

### POURQUOI LES CSS ?

#### Les avantages des CSS

7 termes clés décrivent parfaitement les feuilles de styles :

**Universalité** : on conserve la structure logique, hiérarchique et sémantique du document quelle que soit la plateforme.
**Productivité** : du fait de la séparation du contenu et de la mise en forme, il est plus facile d’effectuer des opérations de création et de maintenance des pages
**Légèreté des pages** : le faible poids entraine une rapidité accrue (logique )
**Accessibilité** : pour les personnes souffrant d’un handicap, pour les robots et les nouveaux dispositifs d’accès, la séparation contenu/mise en forme est capitale.
**Créativité** : Des dizaines et des dizaines de nouvelles règles vont vous offrir des possibilités presque infinies de mise en page et de design.
**Compatibilité** : la concision et la standardisation des règles offre une plus grande compatibilité cross-browser mais ce n’est toujours pas parfait.
**Simplicité** : tout semble plus cohérent, plus logique. Les nouvelles règles sont exploitées rapidement et facilement.

### Les faiblesses des CSS

Parce que rien n’est toujours tout rose, CSS a aussi quelques défauts.

L’un des principaux défauts des CSS est qu’ils sont en constante évolution. Nous avons en effet connu 3 version en un temps assez court : CSS1, CSS2 et maintenant CSS3 (toujours en cours de développement).

Chacune de ces versions apporte son lot de commandes et de nouveautés syntaxiques. Prudence, tous les navigateurs ne sont pas aptes à interpréter les différentes versions. Il y a donc des problèmes de compatibilité.

Comme toujours, de nombreux tests sont donc nécessaires !

### Principe général
Le principe est assez simple :
1. On crée des pages HTML valides en se servant exclusivement de balises sémantiques (h1, p, strong, nav, header, footer, …) dont on veille à conserver le sens et la hiérarchie.
2. On crée une série de styles CSS afin de « re-styler » la manière dont le parseur affiche ces balises sémantiques.


### Principes secondaires
Les principes secondaires qui suivent sont à comprendre parfaitement :
1. Les déclarations de styles CSS comprennent un sélecteur (qui désigne ce qui doit être re-stylé) et une déclaration de propriétés (qui décrit comment cela doit être re-stylé).
2. Pour que les styles CSS s’appliquent aux pages HTML, il faut choisir une méthode d’intégration, plus ou moins centralisée (valable pour une partie de la page, la page entière, plusieurs pages ou toutes les pages).
3. Pour utiliser certains sélecteurs adaptés aux exceptions et cas particuliers, il est nécessaire de compléter les pages HTML avec des balises et/ou attributs spéciaux. Ceci permet l’application correcte des styles.
4. L’interprétation des CSS par le parseur se base sur des règles de gestion des priorités entre les styles.


### ÉTAPES PRÉLIMINAIRES

Dans un monde idéal, voici les quelques étapes préparatoires que vous devriez être amenés à suivre pour créer un site ou une page.

#### Préparation de la maquette
1. On crée d’abord un layout le plus homogène et cohérent possible.
2. On structure la page en plusieurs zones distinctes (titre, navigation principale, navigation secondaire, contenu, pied de page, …)
3. On maintient un nombre raisonnable de styles.

#### Préparation de la page HTML
Les pages HTML auxquelles s’appliquent les CSS doivent se baser sur un codage exclusivement sémantique.

Vous veillerez donc à n’utiliser que des balises porteuses de sens (h1, p, strong, em, …)

 On garde toujours en tête les règles élémentaires de conception d’une page classique et on veille à ce que sa structure soit valide : - Respect de la hiérarchie des titres (h1 est plus fort que h2 qui est plus fort que h3 etc.) - Respect de la syntaxe d’écriture et d’imbrication des balises (```<ul><li> …</li></ul>```) - Fermeture des balises (```<p>…</p>```) Ça peut paraître un peu ringard de rappeler ces 3 règles de bases, mais croyez-moi vous ferez des erreurs de ce style encore pendant un bon moment (on parie ? ^^)

Les techniques héritées du passé (tableaux de mise en forme, pixel transparent, texte sous forme d’image, …) doivent être évitées autant que possible.

On peut encore utiliser les tableaux mais uniquement pour présenter des données tabulaires (ex : un rapport annuel, des statistiques, etc.).


#### Application de styles

3 techniques différentes vont vous permettre d’appliquer un style à un élément html. Chacune est utilisée dans un cas précis :
- **CSS en ligne** : cette technique consiste à placer un attribut style directement à l’intérieur d’une balise. On utilise cette technique uniquement pour la réalisation de newsletters.
```html
<p style="color:red">Un paragraphe rouge</p>
```
- **CSS dans la balise ```<head>```** : cette technique consiste à placer toutes les propriétés CSS entre les balises ```<style></style>``` directement dans le ```<head>``` de votre document HTML.
```html
<style>p {color:red}</style>
```
- **Fichier CSS lié dans la balise ```<head>```** : cette technique consiste à placer un « lien » vers une feuille de style dans le <head> de votre document XHTML.
```html
<link href="style.css" rel="stylesheet" type="text/css" />
```
Vous veillerez à faire attention au chemin relatif indiqué dans l’attribut href afin que le fichier CSS soit bien placé par rapport au fichier .html dans lequel il a été lié.
Les 2 autres attributs, rel et type sont obligatoires et invariables.
Vous pouvez lier autant de fichiers CSS que voulu, pour éventuellement séparer certains styles d’autres.

**C’est évidemment cette façon d’ajouter des styles qui sera toujours employée pour la création de site web tandis qu’employer des CSS « en ligne » est encore utilisé pour les newsletters.**

### LA DÉCLARATION DE STYLE

####Syntaxe générale

La syntaxe de la déclaration de style se présente comme ceci :
```css
sélecteur { déclaration de propriété }
```

ou plus précisément :
```css
sélecteur {
  propriété1:valeur;
  propriété2:valeur;
  …
}
```
**Attention aux détails**
- La déclaration de propriétés est entourée par des accolades { } et non par des crochets [ ] ou des parenthèses ( ).
- Le couple « propriété de style : valeur ; » est séparé par un double point :
- La valeur ne doit pas être entourée par des guillemets " "
- Chaque couple « propriété de style : valeur ; » est séparé par un point-virgule ; Seule la dernière déclaration ne nécessite pas de point-virgule
- Il n’y a pas de limite de nombre de règles CSS dans une déclaration.
- Les espaces dans une déclaration de propriétés ne sont pas obligatoires mais aident fortement à la lisibilité du code source.

Exemple :
Déclaration de style redéfinissant la balise ```<h1>``` :
```css
h1 {
  font-family: Arial;
  font-size: 24px;
  font-style: italic;
  color: #ff0000;
}
```
À travers cette déclaration, on spécifie la police, la taille, l’inclinaison et la couleur du texte balisé par ```<h1>```.

Dans cet exemple, ```<h1>``` est donc re-stylé pour s’afficher en Arial, 24 points, italique et rouge.

Plutôt simple non ?

Quelques commentaires s’imposent néanmoins…

**Insensibilité à la casse**
Les CSS ne sont pas sensibles à la casse que ce soit pour l’écriture des sélecteurs, propriétés ou valeurs.
Cependant les éléments qui ne sont pas propres aux CSS, comme les noms de police ou les URLs, peuvent être sensibles à la casse. Par exemple, pour certains systèmes d'exploitation (tel que Unix), ‘Arial’ n'est pas égal à ‘arial’, de même ‘IMAGE.gif’ n'est pas égal à ‘image.gif’ ! Dans le même esprit que celui du HTML, certains codeurs ont pris l’habitude de taper toutes leurs commandes CSS en minuscule.

**Insensibilité aux sauts de ligne**
La déclaration de style peut s'écrire aussi bien sur une ligne :
```css
h3 { font-family: Arial;font-style: italic; color: #00ff00}
```
… que sur plusieurs lignes (plus lisible):
```css
h3 {
  font-family: Arial;
  font-style: italic;
  color: #00ff00
}
```

### Les commentaires
Il est également possible de commenter ses déclarations de style avec la syntaxe :
```css
/* Ceci est un commentaire */
```

Pour rappel, tout ce qui se trouve entre commentaires ne sera jamais visible par les utilisateurs. En revanche, il est important de commenter vos pages pour vous-même :

- Si vous travaillez sur vos pages à des périodes assez espacées
- Si vous travaillez à plusieurs personnes sur la même page
- Par soucis de clarté et de structure

### LA DECFLARATION DE style

#### Mission du sélecteur
Dans une déclaration de style, le sélecteur désigne ce qui doit être re-stylé dans la page HTML. Il doit donc pouvoir apporter le degré de précision adapté à chaque situation.
C’est la raison pour laquelle il existe plusieurs types de sélecteurs répondants chacun à des besoins particuliers.
Chaque type de sélecteur est reconnaissable syntaxiquement et c’est justement par cette syntaxe qu’il gagne en précision et en concision.

#### Les différents types de sélecteurs
Voici les différents sélecteurs disponibles jusqu’à la version 2.0 de CSS (de nouveaux sélecteurs arrivent avec CSS 3.0) :

1. Le sélecteur universel : *
2. Le sélecteur de type : X
3. Le sélecteur d’attribut : balise[attribut]
4. Le sélecteur de classe :..maclasse
5. Le sélecteur d’ID : #monid
6. Le sélecteur descendant : X Y
7. Le sélecteur adjacent : X + Y
8. Le sélecteur d’enfant : X > Y
9. Les pseudo-éléments : :before et :after
10. Les pseudo-éléments : :first-line et :first-letter
11. Les pseudo-classes : :link, :visited, :hover et :active
12. Le pseudo-classes : :first-child et :focus

1. Le sélecteur universel
Le sélecteur universel sélectionne indifféremment toutes les balises d’un document. C’est le sélecteur le plus puissant mais aussi le moins précis.
Il se présente comme suit :
```css
* { déclaration de propriétés }
```
Exemple :
```css
* { margin: 0; padding: 0; }
```
Les marges internes et externes par défaut de toutes(\*) les balises du document sont supprimées.

2. Le sélecteur de type (de balise)
Toutes les balises sémantiques peuvent servir de sélecteur, absolument TOUTES !
```<html>```, ```<body>```, ```<p>```, ```<a>```, ```<input>```, ```<table>```, ```<tr```>, ```<td>```, ```<strong>```, ```<em>```, ```<ul>```, ```<ol>```, ```<li>```, ```<img>```, etc.
Exemple :
```css
p {
  line-height: 2em;
  border-left-width: thick;
  padding-left: 25px;
}
```
Dans cet exemple, les balises p du document sont re-stylées avec un interlignage correspondant à 2 fois la taille du texte par défaut. De plus, un filet épais apparaît sur le côté gauche du paragraphe, à une distance de 25px.

3. Le sélecteur d’attribut
Les sélecteurs d’attributs permettent d’appliquer un style en fonction de la valeur de l’attribut de la balise HTML. Ils prennent la forme suivante :
```css
balise[attribut="valeur"] { … }
```
Exemple :
```css
hr[size="3"] { width: 50%; }
```

Le style (largeur fixée à 50%) ne sera appliqué qu’aux filets horizontaux dont l’épaisseur est de 3.

4. Le sélecteur de classe

Les classes permettent de cibler l’application d’un style en lui attribuant un nom. Elles permettent de gérer les cas particuliers et les exceptions.
```css
.nom_de_la_classe { … }
```
Elles sont ensuite appelées dans le document avec l’attribut class :
```html
<balise class="nom_de_la_classe">…</balise>
```
**Le choix du nom de la classe**
Seules les balises appelant la classe appliqueront son style. Le choix du nom pour les classes est libre. Toutefois, les noms des classes ne peuvent contenir que les lettres de a-z ou de A-Z, les chiffres de 0-9, le trait d'union (-) et le caractère souligné (\_). Les noms ne peuvent pas commencer par un chiffre ou un tiret.

Exemple :
Je souhaite faire ressortir ce qui est très important dans un document. Je crée la classe essentiel à laquelle j’associe un style spécifique (gras et bleu)…
```css
.essentiel { font-weight: bold; color: #000080; }
```
Dans le document Html, il suffit d'appeler la classe essentiel quand cela s'avère nécessaire :
```html
<h1 class="essentiel"> ... blabla ... </h1>
<p> ... blabla ... </p>
<p class="essentiel"> ... blabla ... <p>
  <table>
    <tr>
      <td class="essentiel"> ... </td>
    </tr>
  </table>
  ```
Pour limiter la portée d’une classe, on peut lors de sa définition la restreindre à n’être appelée que par une balise particulière :
```css
baliseX.nom_de_la_classe { … }
```
Dans le document, la classe ne peut être appelée que dans la balise spécifiée.
```html
<baliseX class="nom_de_la_classe">…</baliseX>
```
Si la classe est appelée dans une autre balise, le parseur n'applique pas la classe.
```html
<baliseY class="nom_de_la_classe">…</baliseY>
```
Exemple :
On crée la classe super associée à la balise h1…
```css
h1.super { font-size: 12pt; font-weight: bold; }
```
On peut ensuite appeler la classe dans la page Web…
```html
<h1 class="super"> …blabla… </h1>
```
Mais, attention :
```html
<h2 class="super"> …blabla… </h2>
```
Cette déclaration sera sans effet car la classe super n’a pas été associée à h2 dans la déclaration de style.
Avec cette écriture plus restrictive des classes, car liée à une balise spécifique, rien n’empêche d’utiliser plusieurs fois le même nom de classe avec des balises différentes.
```css
h1.super { font-size: 12pt; font-weight: bold; }
h2.super { font-size: 10pt; font-weight: normal; }
h3.super { font-size: 8pt; font-style: italic; }
```
Il s’agit bien ici de trois sélecteurs différents.

5. Le sélecteur d’ID

Comparables aux classes, les ID permettent de cibler l’application d’un style en lui attribuant un nom. Elles permettent donc aussi de gérer les cas particuliers et les exceptions. Les ID se présentent comme suit…
```css
#nom_de_l’ID { … }
```
Le choix du nom de l’ID doit respecter les mêmes restrictions que pour les classes.
Les ID sont ensuite appelées dans le document avec l’attribut id :
```html
<balise id="nom_de_l’ID">…</balise>
```
Tout comme pour les classes, pour limiter sa portée, une ID peut voir son appel restreint à une balise particulière…
```css
baliseX#nom_de_l’ID { … }
```
Dans le document, la classe ne peut être appelée que dans la balise spécifiée.
```html
<baliseX id="nom_de_l’ID">…</baliseX>
```
A première vue, Classes et ID remplissent la même fonction.
**Mais attention, une ID ne peut être appelée qu’une seule fois par document !**
Prenons la déclaration suivante : ```#essentiel { ... }```
Dans le document, l’appel ```<p id="essentiel">``` est correct. Mais si on rencontre un peu plus loin, dans le même document, ```<h1 id="essentiel">```… le document n’est plus valide !

Du fait de cette contrainte, on voit mal pourquoi ne pas abandonner les ID au profit des Classes qui sont beaucoup plus souples. Nous verrons que cette contrainte peut être un avantage lorsque l’on combine les ID avec certaines formes syntaxiques de sélecteur. Affaire à suivre, donc…

6. Le sélecteur descendant
Le sélecteur de descendance permet d’appliquer un style à la balise fille d’un parent (imbrication). On sépare chaque élément par un espace blanc. Cela se présente comme ceci :
```css
électeurA sélecteurB { … }
```
Exemple :
```css
p strong { border: solid 1px #999; }
```
Appliquera une bordure dans le document à...
```html
<p>…<strong> Cible </strong>…</p>
```
mais pas à...
```html
<h1>...<strong>blabla</strong>...</h1>
```
Le sélecteur de descendance associé avec des ID offre beaucoup de précision et de puissance. En effet, lorsque la page est découpée en zones associées à des ID uniques (#en-tete, #menu, #contenu, #footer…), on peut utiliser dans chacune des zones les mêmes balises sémantiques ou les mêmes classes sans qu’elles n’aient le même style.

Avec quelques zones et un nombre réduit de balises sémantiques, on peut varier facilement les styles!

Exemples :
```css
#en-tete p { font-size: 12pt; font-weight: bold; }
#en-tete a { color: #00f; text-decoration: none; }
#contenu p { font-size: 10pt; line-height: 1.4em; }
#contenu a { color: #000; font-style: italic; }
```
7. Le sélecteur adjacent
Le sélecteur adjacent permet d’appliquer un style à la balise suivant immédiatement une autre balise. Il se présente comme suit :
```css
sélecteur A + sélecteurB { … }
```
Exemple :
```css
h1 + p { color : blue }
```
Dans ce document HTML :
```html
<h1>… blabla …</h1> <p>Cible</p> <p>… blabla …</p>
```
Il faut donc lire la déclaration comme suit : « à partir d’un \<h1\>, la première balise \<p\> aura le style suivant ». Et si vous voulez cibler le 2e paragraphe, rien de plus simple :
```css
h1 + p + p { color:blue; }
```

8. Le sélecteur d’enfant direct
Le sélecteur d’enfant permet de sélectionner l’enfant direct d’une balise. Il se présente comme suit :
```css
sélecteur A > sélecteurB { … }
```
Exemple : div > p {color: #CB000F;}
Dans ce document HTML : <div> <p>Test d'un paragraphe dans un div</p> <section> <p>Test d'un paragraphe dans une section</p> </section> </div>
Voilà le résultat obtenu :
Le sélecteur n’agit donc que sur le tout premier élément <strong> et pas sur tous ceux qui sont inclus en lui comme c’était le cas avec le sélecteur descendant.
