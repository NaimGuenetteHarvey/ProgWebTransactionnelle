Sélecteurs jQuery

Les sélecteurs servent à repérer les éléments HTML qu’on veut manipuler.

Sélecteur	Sélectionne...	   Exemple
$("p")	                     Tous les <p>	tous les paragraphes
$("#faqs")	                 L’élément avec id="faqs"	un seul élément
$(".plus")	                 Tous les éléments avec class="plus"	plusieurs éléments
$("#faqs").find("p")	       Tous les <p> à l’intérieur de #faqs	descendants
$("h2.minus")	               Tous les <h2> ayant class="minus"	éléments combinés
$("h2 + div")	               Le <div> juste après un <h2>	frère adjacent
div > ul	                   Tous les <ul> enfants directs de <div>	relation parent-enfant
#faqs li, div p	             Tous les <li> dans #faqs et les <p> dans un <div>	sélection multiple

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Filtres jQUERY... 
« Les filtres jQuery permettent de sélectionner de manière plus précise certains éléments parmi un ensemble d’éléments déjà ciblés, selon leur position, leur contenu, leur attribut ou leur état (visible, caché, vide, etc.). »

###1. [attribute]

But : Sélectionne tous les éléments qui possèdent un certain attribut.
Exemple : [href] sélectionne tous les éléments qui ont un attribut href.

<a href="https://google.com">Google</a>
<a>Sans lien</a>

<script>
$("[href]").css("color", "red");
</script>
 Tous les liens avec un href deviennent rouges.


###2. [attribute=value]

But : Sélectionne les éléments dont l’attribut a une valeur spécifique.

<input type="text">
<input type="password">

<script>
$("[type='password']").css("border", "2px solid red");
</script>

Les champs password auront une bordure rouge.


###3. :empty

But : Sélectionne les éléments qui ne contiennent rien (ni texte, ni enfant).

<div id="plein">Salut</div>
<div id="vide"></div>

<script>
$("div:empty").css("background", "yellow");
</script>
 Le <div> vide devient jaune.


###4. :eq(n)

But : Sélectionne l’élément à l’index n dans un ensemble (le premier est 0).

<ul>
  <li>Élément 0</li>
  <li>Élément 1</li>
  <li>Élément 2</li>
</ul>

<script>
$("li:eq(1)").css("color", "blue");
</script>

Le 2ᵉ élément (index 1) devient bleu.


###5. :even

But : Sélectionne les éléments pairs (index 0, 2, 4…).

<table>
  <tr><td>Ligne 1</td></tr>
  <tr><td>Ligne 2</td></tr>
  <tr><td>Ligne 3</td></tr>
  <tr><td>Ligne 4</td></tr>
</table>

<script>
$("tr:even").css("background", "#eee");
</script>


Les lignes 1 et 3 (index 0 et 2) ont un fond gris clair.


###6. :odd

But : Sélectionne les éléments impairs (index 1, 3, 5…).

<tr><td>Ligne 1</td></tr>
<tr><td>Ligne 2</td></tr>
<tr><td>Ligne 3</td></tr>

<script>
$("tr:odd").css("background", "#ccc");
</script>

Les lignes 2 et 4 deviennent grises foncées.



###7. :first

But : Sélectionne le premier élément d’un ensemble.

<p>Premier</p>
<p>Deuxième</p>

<script>
$("p:first").css("font-weight", "bold");
</script>

Le premier paragraphe devient en gras.



###8. :first-child

But : Sélectionne tous les éléments qui sont le premier enfant de leur parent.

<ul>
  <li>Premier</li>
  <li>Deuxième</li>
</ul>
<ul>
  <li>Encore premier</li>
  <li>Encore deuxième</li>
</ul>

<script>
$("li:first-child").css("color", "green");
</script>

Le premier <li> de chaque liste devient vert.


###9. :header

But : Sélectionne tous les titres (<h1> à <h6>).

<h1>Titre 1</h1>
<h2>Titre 2</h2>
<p>Paragraphe</p>

<script>
$(":header").css("text-decoration", "underline");
</script>

Tous les titres sont soulignés.



###10. :hidden

But : Sélectionne tous les éléments masqués (display:none).

<p id="cache" style="display:none;">Caché</p>
<p id="visible">Visible</p>

<script>
$(":hidden").show(); // rend visible
</script>

Le paragraphe caché devient visible.




###11. :visible

But : Sélectionne tous les éléments visibles.

<p style="display:none;">Caché</p>
<p>Visible</p>

<script>
$(":visible").css("color", "orange");
</script>

Le paragraphe visible devient orange.



###12. :not(selector)

But : Sélectionne tous les éléments sauf ceux qui correspondent au sélecteur.

<div class="actif">Actif</div>
<div>Inactif</div>

<script>
$("div:not(.actif)").css("background", "pink");
</script>

Tous les <div> sauf celui avec la classe .actif deviennent roses.



###13. :parent

But : Sélectionne tous les éléments qui contiennent du texte ou des enfants.

<div>Contenu</div>
<div></div>

<script>
$("div:parent").css("border", "2px solid green");
</script>

Seul le <div> qui a du contenu obtient une bordure verte.
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------
MÉTHODE JQUERY...

1. .css() – Modifier ou lire le style
<p id="monParagraphe">Texte normal</p>

<script>
  // Changer la couleur
  $("#monParagraphe").css("color", "blue");

  // Lire la couleur actuelle
  let couleur = $("#monParagraphe").css("color");
  console.log("Couleur actuelle :", couleur);
</script>


Explication :
.css("propriété", "valeur") change le style.
.css("propriété") récupère la valeur actuelle.


2. .attr() – Modifier ou lire un attribut
<img id="monImage" src="image1.jpg" alt="Image">

<script>
  // Changer l'attribut src
  $("#monImage").attr("src", "image2.jpg");

  // Lire l'attribut alt
  let altTexte = $("#monImage").attr("alt");
  console.log("Texte alt :", altTexte);
</script>


Explication :
.attr("nom", "valeur") modifie ou ajoute un attribut.
.attr("nom") lit la valeur de l’attribut.


3. .next() et .prev() – Naviguer entre frères
<h2>Titre 1</h2>
<div>Contenu 1</div>

<script>
  // Sélectionner le div qui suit le h2
  $("h2").next().css("color", "red");

  // Sélectionner le h2 avant le div
  $("div").prev().css("text-decoration", "underline");
</script>


Explication :
.next() : frère suivant.
.prev() : frère précédent.


4. .val() – Lire ou changer la valeur d’un champ
<input type="text" id="nom" value="Alice">
<button id="btn">Changer valeur</button>

<script>
  // Lire la valeur
  console.log($("#nom").val());

  // Changer la valeur au clic
  $("#btn").click(function() {
    $("#nom").val("Bob");
  });
</script>


Explication :
.val() récupère la valeur.
.val("nouvelleValeur") change la valeur.


5. .text() – Lire ou changer le texte
<p id="monParagraphe">Bonjour</p>
<button id="changerTexte">Changer</button>

<script>
  console.log($("#monParagraphe").text()); // lit le texte

  $("#changerTexte").click(function() {
    $("#monParagraphe").text("Salut jQuery !");
  });
</script>


Explication :
.text() lit le texte à l’intérieur.
.text("nouveau texte") change le texte.


6. .on() – Ajouter un événement
<button id="monBouton">Clique-moi</button>

<script>
  $("#monBouton").on("click", function() {
    alert("Bouton cliqué !");
  });
</script>


Explication :
.on("événement", fonction) attache un événement à l’élément.


7. .off() – Retirer un événement
<button id="btn2">Désactiver clic</button>

<script>
  function clicHandler() { alert("Clic actif !"); }

  $("#btn2").on("click", clicHandler); // ajoute l’événement
  $("#btn2").off("click", clicHandler); // le retire
</script>


Explication :
.off() supprime l’événement attaché.


8. .one() – Événement une seule fois
<button id="btnOne">Clique une fois</button>

<script>
  $("#btnOne").one("click", function() {
    alert("Message affiché une seule fois !");
  });
</script>


Explication :
L’événement ne se déclenche qu’une seule fois.


9. .trigger() – Déclencher un événement manuellement
<button id="btnClick">Clic normal</button>
<button id="btnTrigger">Déclenche clic</button>

<script>
  $("#btnClick").on("click", function() {
    alert("Clic déclenché !");
  });

  $("#btnTrigger").click(function() {
    $("#btnClick").trigger("click"); // simule un clic
  });
</script>


Explication :
.trigger("événement") déclenche un événement comme si l’utilisateur l’avait fa
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Méthodes d’attributs et de styles...

1️ attr("nom") – Lire un attribut
<img id="photo" src="chat.jpg" alt="Un chat">

<script>
  let source = $("#photo").attr("src");
  console.log("Source de l'image :", source);
</script>


Explication :
Récupère la valeur de l’attribut "src" de l’image.
Ici, source contiendra "chat.jpg".



2️ attr("nom", "valeur") – Modifier ou ajouter un attribut
<img id="photo2" src="chien.jpg" alt="">

<script>
  $("#photo2").attr("alt", "Un chien mignon");
</script>


Explication :
Change ou ajoute l’attribut "alt" de l’image.
Résultat : alt="Un chien mignon".



3️ css("propriété") – Lire une propriété CSS
<p id="texte1" style="color: red;">Bonjour</p>

<script>
  let couleur = $("#texte1").css("color");
  console.log("Couleur :", couleur);
</script>


Explication :
Récupère la couleur actuelle du texte (ici "red").



4 css("propriété", "valeur") – Modifier une propriété CSS
<p id="texte2">Salut !</p>

<script>
  $("#texte2").css("color", "blue");
</script>

Explication :
Change la couleur du texte en bleu.
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Méthodes d’événements...


1️ ready(handler) – Exécuter quand la page est prête
<p id="demo">Texte</p>

<script>
$(document).ready(function() {
  $("#demo").css("color", "green");
});
</script>


Explication :
Le code à l’intérieur s’exécute une fois que la page est complètement chargée.


2️ click(handler) – Réagir au clic
<button id="btnClick">Clique-moi</button>

<script>
$("#btnClick").click(function() {
  alert("Bouton cliqué !");
});
</script>


Explication :
Exécute la fonction dès qu’on clique sur le bouton.



3️ on(event, handler) – Attacher un événement
<p id="para">Passe la souris ici</p>

<script>
$("#para").on("mouseenter", function() {
  $(this).css("color", "orange");
});
</script>


Explication :
Permet de réagir à n’importe quel événement, ici au survol (mouseenter).



4️ off(event, handler) – Supprimer un événement
<p id="para2">Clique ici</p>

<script>
function clicHandler() {
  alert("Clic actif !");
}

$("#para2").on("click", clicHandler); // ajoute l’événement
$("#para2").off("click", clicHandler); // supprime l’événement
</script>


Explication :
Retire le gestionnaire de l’événement attaché précédemment.



5️ one(event, handler) – Événement une seule fois
<button id="btnOnce">Clique une fois</button>

<script>
$("#btnOnce").one("click", function() {
  alert("Ce message n'apparait qu'une seule fois !");
});
</script>


Explication :

La fonction ne sera exécutée qu’une seule fois, puis l’événement est supprimé.



6️ trigger(event) – Déclencher un événement manuellement
<button id="btnNormal">Clic normal</button>
<button id="btnTrigger">Déclencher clic</button>

<script>
$("#btnNormal").on("click", function() {
  alert("Bouton normal cliqué !");
});

$("#btnTrigger").click(function() {
  $("#btnNormal").trigger("click");
});
</script>


Explication :
Le deuxième bouton simule un clic sur le premier bouton, déclenchant l’alerte.
