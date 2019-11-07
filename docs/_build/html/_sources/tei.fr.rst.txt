.. _tei-fr:

Documentation (français)
##########################################

Ce document présente les spécifications pour le balisage XML de
documents en vue de leur importation dans Lodel 1.0. Les Xpath proposés
ici sont définis dans le modèle éditorial de OpenEdition et dans le
schéma tei.openedition défini dans ce projet Github.

| La prise en compte d'une structuration des documents conforme aux
  standards TEI est une des spécificités et un point-clé de LODEL. Pour
  en savoir plus sur TEI, visitez `le site de la Text Encoding
  Initiative <http://www.tei-c.org/>`__.
| Le schéma XML W3C pour l'encodage TEI Openedition est disponible à
  l'adresse http://lodel.org/ns/.
| Un document TEI d'exemple est disponible à cette adresse :
  `Lorem-ipsum-Lodel1.0.xml <https://github.com/OpenEdition/tei.openedition/blob/master/doc/lorem_ipsum_lodel_1.0.xml>`__.

.. toctree::
   :maxdepth: 5
   :numbered: 2
   :caption: TEI

   tei.fr.teiHeader.rst




.. _tei-fr-text:

text
====

front
-----

Résumés
~~~~~~~

*Xpath*:

-  Résumés :
   ``/tei:TEI/tei:text/tei:front/tei:div[@type='abstract' and @xml:lang]``
   Comme pour les titres traduits, l'attribut ``xml:lang`` est
   obligatoire avec un valeur au format ISO 639-1.

*Exemple*:

.. code:: xml

   [...]
   <text>
       <front>
   [...]
           <div type="abstract" xml:lang="fr">
               <p>Il était sur le dos, un dos aussi dur qu’une carapace, et, en relevant un peu la tête, il vit, bombé, brun, cloisonné par des arceaux plus rigides, son abdomen sur le haut duquel la couverture, prête à glisser tout à fait, ne tenait plus qu’à peine. Ses nombreuses pattes, lamentablement grêles par comparaison avec la corpulence qu’il avait par ailleurs, grouillaient désespérément sous ses yeux. « Qu’est-ce qui m’est arrivé ? » pensa-t-il.</p>
               <p>Ce n’était pas un rêve. [...]</p>
           </div>
           <div type="abstract" xml:lang="en">
               <p>"Oh, God", he thought, "what a strenuous career it is that I've chosen! Travelling day in and day out. Doing business like this takes much more effort than doing your own business at home, and on top of that there's the curse of travelling, worries about making train connections, bad and irregular food, contact with different people all the time so that you can never get to know anyone or become friendly with them. It can all go to Hell! "He felt a slight itch up on his belly; pushed himself slowly up on his back towards the headboard so that he could lift his head better; found where the itch was, and saw that it was covered with lots of little white spots which he didn't know what to make of; and when he tried to feel the place with one of his legs he drew it quickly back because as soon as he touched it he was overcome by a cold shudder. He slid back into his former position. "Getting up early all the time", he thought, "it makes you stupid. You've got to get enough sleep. Other travelling salesmen live a life of luxury. For instance, whenever I go back to the guest house during the morning to copy out the contract, these gentlemen are always still sitting there eating their breakfasts. I ought to just try that with my boss; I'd get kicked out on the spot. But who knows, maybe that would be the best thing for me. If I didn't have my parents to think about I'd have given in my notice a long time ago, I'd have gone up to the boss and told him just what I think, tell him everything I would, let him know just what I feel. He'd fall right off his desk! And it's a funny sort of business to be sitting up there at your desk, talking down at your subordinates from up there, especially when you have to go right up close because the boss is hard of hearing. Well, there's still some hope; once I've got the money together to pay off my parents' debt to him - another five or six years I suppose - that's definitely what I'll do. That's when I'll make the big change.</p>
           </div>
           <div type="abstract" xml:lang="es">
               <p>Las preocupaciones son mucho mayores cuando se trabaja fuera, por no hablar de las molestias propias de los viajes: estar pendiente de los enlaces de los trenes; la comida mala, irregular; relaciones que cambian constantemente, que nunca llegan a ser verdaderamente cordiales, y en las que no tienen cabida los sentimientos. amsa era viajante de comercio-, y de la pared colgaba una estampa recientemente recortada de una revista ilustrada y puesta en un marco dorado.</p>
           </div>
   [...]

Notes de lecture et comptes rendus d’ouvrages
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Les notes de lecture et comptes rendus d’ouvrages sont à styler
séparément en autant de fichiers. Ne pas intituler ce type de document «
Note de lecture ».

Si la recension n’a pas de titre propre, il est d’usage d’appliquer le
style « Titre » à l’auteur et au titre de l’ouvrage recensé. Il est
aussi possible de styler les éléments bibliographiques (éditeur, lieu et
année d’édition…) en « Sous-titre » : ceci permet d’afficher la notice
bibliographique dans le sommaire.

Les titre, nom d’auteur, notice bibliographique et date de publication
des œuvres commentées peuvent aussi être stylés en tant qu’élément
descriptif du document.

Ces informations permettront un meilleur référencement et donneront la
possibilité de créer des index spécifiques (index des auteurs des œuvres
commentées par exemple). L’affichage de ces informations dans la
maquette peut aussi être prévu.

Ces indications ne remplacent pas le titre du document. Il est
nécessaire d’indiquer ce dernier, même s’il reprend les éléments
indiqués par les styles « œuvre commentée ».

*Xpath*:

-  Titre de l’œuvre commentée :
   ``/tei:TEI/tei:text/tei:front/tei:div[@type='review']/tei:p[@rend='review-title']``
-  Auteur de l’œuvre commentée :
   ``/tei:TEI/tei:text/tei:front/tei:div[@type='review']/tei:p[@rend='review-author']``
-  Notice bibliographique de l’œuvre commentée :
   ``/tei:TEI/tei:text/tei:front/tei:div[@type='review']/tei:p[@rend='review-bibliography']``
-  Date de publication de l’œuvre commentée :
   ``/tei:TEI/tei:text/tei:front/tei:div[@type='review']/tei:p[@rend='review-date']``

*Exemple*:

.. code:: xml

   [...]
   <text>
       <front>
   [...]
           <div type="review">
               <p rend="review-title">La métamorphose</p>
               <p rend="review-author">Franz Kafka</p>
               <p rend="review-bibliography">Franz Kafka, <hi rend="italic">La métaporphose</hi> [1938] , trad. de l'allemand par Alexandre Vialatte, 224 pages, 140 x 205 mm. Collection Du monde entier, Gallimard-nouv. ISBN 2070235157.</p>
               <p rend="review-date">1938</p>
           </div>
   [...]

Note de l’auteur, note de la rédaction, erratum, remerciements
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

*Xpath*:

-  Note de l’auteur :
   ``/tei:TEI/tei:text/tei:front/tei:note[@resp='author']/tei:p``
-  Note de la rédaction :
   ``/tei:TEI/tei:text/tei:front/tei:note[@resp='editor']/tei:p``
-  Erratum :
   ``/tei:TEI/tei:text/tei:front/tei:div[@type='correction']/tei:p``
-  Dédicace :
   ``/tei:TEI/tei:text/tei:front/tei:div[@type='dedication']/tei:p``
-  Remerciements :
   ``/tei:TEI/tei:text/tei:front/tei:div[@type='ack']/tei:p``

*Exemple*:

.. code:: xml

   [...]
   <text>
       <front>
   [...]
           <div type="ack">
               <p>Je remercie le site Blind Text Generator qui a fourni tout le faux-texte de ce document.</p>
           </div>
           <div type="correction">
               <p>L'erratum permet de signaler les modifications apportées au texte après sa publication.</p>
           </div>
           <note resp="editor">
               <p>
                   Le texte de ce document a été généré sur le site <ref target="http://www.blindtextgenerator.com/">http://www.blindtextgenerator.com</​ref>.
               </p>
           </note>
           <note resp="author">
               <p>
                   Les résumés français, anglais et espagnol sont des extraits de <hi rend="italic">La Métamorphose</hi> de Franz Kafka.
               </p>
           </note>
       </front>
   [...]

body
----

Structure du texte et intertitres
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Le texte du document doit être structuré par des sections (balises div).

Les intertitres doivent être indiqués comme premier élément de la
section dans une balise head avec un attribut de la forme
``subtype="level1"``

*Exemple*:

.. code:: xml

   <text>
           <div>
               <head subtype="level1">1. ...</head>
               <div>
                   <head subtype="level2">1.1. ...</head>
                   <p>...</p>
                   <div>
                       <head subtype="level3">1.1.1. ...</head>
                       <p>...</p>
                   </div>
                   <div>
                       <head subtype="level3">1.1.2. ...</head>
                       <p>...</p>
                   </div>
               </div>
               <div>
                   <head  subtype="level2">1.2. ...</head>
                   <p>...</p>
               </div>
           </div>
           <div>
               <head subtype="level1">2. ...</head>
               <p>...</p>
           </div>
   [...]

Notes de bas de page et notes de fin
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Elles doivent être insérées dans le texte, dans des balises ``<note>``
avec un attribut place pour indiquer le type de note et un attribut n
pour indiquer le numéro de la note. Le contenu de la note doit
impérativement être placé dans un ou plusieurs paragraphes.

*Xpath*:

-  Note de bas de page : ``//tei:note[@place='foot' and @n]/tei:p``
-  Note de fin : ``//tei:note[@place='end'and @n]/tei:p``

*Exemple*:

.. code:: xml

   [...] 
   Curabitur ullamcorper ultricies nisi<note place="foot" n="4">
       <p>Nulla consequat massa quis enim.</p>
   </note>. Nam eget dui.<note place="end" n="i">
       <p>Etiam rhoncus.</p>
   </note>
   [...]

*Résultat HTML*:

.. code:: html

   <p class="paragraphesansretrait">Curabitur ullamcorper ultricies nisi<a class="footnotecall" id="bodyftn1" href="#ftn1">4</a>. Nam eget dui.<a class="endnotecall" id="bodyftn2" href="#ftn2">i</a></p>

.. _mises-en-forme-du-texte--balises-hi-attributs-rend-et-rendition:

Mises en forme du texte : balises hi, attributs rend et rendition
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Pour appliquer des mises en forme du texte, il est possible d’utiliser
la balise ``<hi>`` avec un attribut rend ayant pour valeur : ``italic``,
``bold``, ``sup``, ``sub``, ``uppercase``, ``small-caps``, ``underline``

Il est également possible d’utiliser la balise ``<hi>`` avec un attribut
rendition faisant référence à un style défini au format css dans la
header (``/tei:TEI/tei:teiHeader/tei:encodingDesc/tei:tagsDecl``)

*Exemple* :

.. code:: xml

   <teiHeader>
   [...]
         <encodingDesc>
   [...]
             <tagsDecl>
                 <rendition xml:id="T5" scheme="css">font-style:italic;font-weight:bold</rendition>
                 <rendition xml:id="T6" scheme="css">font-style:italic;text-decoration:underline</rendition>
                 <rendition xml:id="T7" scheme="css">font-style:italic;text-decoration:underline;font-weight:bold</rendition>
                 <rendition xml:id="T10" scheme="css">text-decoration:underline;font-weight:bold</rendition>
             </tagsDecl>
         </encodingDesc>
   [...]
   </teiHeader>
   <body>
       <text>
           <div>
               <p>
                   <hi rend="italic">Aenean <hi rend="sup">commodo</hi></hi> ligula eget dolor. Aenean massa. 
                   <hi rendition="#T5">Cum sociis</hi> 
                   natoque 
                   <hi rendition="#T6">penatibus et magnis</hi> 
                   dis 
                   <hi rendition="#T7">parturient montes</hi>, nascetur 
                   <hi rendition="#T10">ridiculus mus</hi>.
               </p>
           </div>
   [...]

*Résultat HTML (rendu)* :

.. raw:: html

   <p><em>Aenean <sup>commodo</sup></em> ligula eget dolor. Aenean massa. <em><strong>Cum sociis</strong></em>                             natoque <em><span style="text-decoration:underline;">penatibus et magnis</span></em>                            dis <em><strong><span style="text-decoration:underline;">parturient montes</span></strong></em>, nascetur <strong><span style="text-decoration:underline;">ridiculus mus</span></strong>.</p>

Citations et styles de paragraphe (question, réponse, paragraphe sans retrait, encadré, épigraphe)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Les styles internes suivants sont déclarés dans le modèle éditorial

-  Citation : ``//tei:q[@rend='quotation']``
-  Citation bis : ``//tei:q[@rend='quotation2']``
-  Citation ter : ``//tei:q[@rend='quotation3']``
-  Question : ``//tei:p[@rend='question']``
-  Réponse : ``//tei:p[@rend='answer']``
-  Paragraphe sans retrait : ``//tei:p[@rend='noindent']``
-  Encadré : ``//tei:p[@rend='box']``
-  Epigraphe : ``//tei:p[@rend='epigraph']``
-  Séparateur : ``//tei:p[@rend='break']``

*Exemple* :

.. code:: xml

   [...]
   <q rend="quotation">
       Citation : Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus condimentum accumsan quam, non hendrerit lacus posuere vel. 
   </q>
   <q rend="quotation2">
       Citation bis : Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus condimentum accumsan quam, non hendrerit lacus posuere vel. 
   </q>
   <q rend="quotation3">
       Citation ter : Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus condimentum accumsan quam, non hendrerit lacus posuere vel.
   </q>
   <p rend="question">
       Question : Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus condimentum accumsan quam, non hendrerit lacus posuere vel.
   </p>
   <p rend="answer">
       Réponse : Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus condimentum accumsan quam, non hendrerit lacus posuere vel.  
   </p>
   <p rend="noindent">
       Paragraphe sans retrait : Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus condimentum accumsan quam, non hendrerit lacus posuere vel. 
   </p>
   <p rend="box">
       Encadré : Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus condimentum accumsan quam, non hendrerit lacus posuere vel. 
   </p>
   <p rend="epigraph">
     <hi rend="italic">En se réveillant un matin après des rêves agités, Gregor Samsa se retrouva, dans son lit, métamorphosé en un monstrueux insecte.</hi>
      <lb />
      Franz Kafka,
       <hi rend="italic">La métamorphose</hi>
     </p>
   <p rend="break">* * *</p>
   [...]

*Résultat HTML* :

.. code:: html

   <blockquote>
    <p class="citation">Citation : Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus condimentum accumsan quam, non hendrerit lacus posuere vel. </p>
   </blockquote>
   <blockquote class="citationbis">
    <p class="citationbis">Citation bis : Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus condimentum accumsan quam, non hendrerit lacus posuere vel. </p>
   </blockquote>
   <blockquote class="citationter">
    <p class="citationter">Citation ter : Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus condimentum accumsan quam, non hendrerit lacus posuere vel.</p>
   </blockquote>
   <p class="question">Question : Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus condimentum accumsan quam, non hendrerit lacus posuere vel.</p>
   <p class="reponse">Réponse : Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus condimentum accumsan quam, non hendrerit lacus posuere vel.  </p>
   <p class="paragraphesansretrait">Paragraphe sans retrait : Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus condimentum accumsan quam, non hendrerit lacus posuere vel. </p>
   <p class="encadre">Encadré : Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus condimentum accumsan quam, non hendrerit lacus posuere vel. </p>
   <p class="epigraphe">              <em>En se réveillant un matin après des rêves agités, Gregor Samsa se retrouva, dans son lit, métamorphosé en un monstrueux insecte.</em>               <br />               Franz Kafka,              <em>La métamorphose</em>            </p>
   <p class="separateur">* * *</p> 

Listes
~~~~~~

Il est possible d'utiliser des listes ordonnées ou non ordonnées et
bien-sûr de les imbriquer.

*Xpath* :

-  Éléments de liste non-ordonnée :
   ``//tei:list[@type='unordered']/tei:item``
-  Éléments de liste ordonnée : ``//tei:list[@type='ordered']/tei:item``

*Exemple* :

.. code:: xml

   [...]
   <list xml:id="list2094761347" type="unordered">
       <item>
           Fusce fermentum.
           <list type="unordered">
               <item>
                   Nullam cursus lacinia erat.
               </item>
               <item>
                   Praesent blandit laoreet nibh. 
               </item>
           </list>
       </item>
       <item>
           Fusce convallis metus id felis luctus adipiscing.
           <list type="ordered">
               <item>
                   Pellentesque egestas, 
               </item>
               <item>
                   neque sit amet convallis pulvinar,
               </item>
               <item>
                   justo nulla eleifend augue, 
               </item>
               <item>
                   ac auctor orci leo non est. 
               </item>
           </list>
       </item>
   </list>
   [...]

*Résultat HTML* :

.. code:: html

   <ul class="texte">
    <li>Fusce fermentum.
     <ul class="texte">
      <li>Nullam cursus lacinia erat.</li>
      <li>Praesent blandit laoreet nibh. </li>
     </ul>
    </li>
    <li>Fusce convallis metus id felis luctus adipiscing.
      <ol class="texte">
       <li>Pellentesque egestas, </li>
       <li>neque sit amet convallis pulvinar,</li>
       <li>justo nulla eleifend augue, </li>
       <li>ac auctor orci leo non est. </li>
     </ol>
    </li>
   </ul>

Types de numérotation ou de puce
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Il est possible de définir un type de numérotation ou de puce en
utilisant un attribut ``rendition`` sur l'élément ``<list>``. Les
valeurs autorisées pour les listes non ordonnées sont :

-  ``list-style-type:disc``
-  ``list-style-type:square``
-  ``list-style-type:circle``

Pour les listes ordonnées :

-  ``list-style-type:decimal``
-  ``list-style-type:lower-roman``
-  ``list-style-type:upper-roman``
-  ``list-style-type:lower-alpha``
-  ``list-style-type:upper-alpha``

*Exemple* :

.. code:: xml

   <teiHeader>
   [...]
           <encodingDesc>
   [...]
               <tagsDecl>
                   <rendition xml:id="list1" scheme="css">list-style-type:upper-roman</rendition>
           <rendition xml:id="list2" scheme="css">list-style-type:lower-roman</rendition>
           <rendition xml:id="list3" scheme="css">list-style-type:lower-alpha</rendition>
           <rendition xml:id="list4" scheme="css">list-style-type:upper-alpha</rendition>
               </tagsDecl>
           </encodingDesc>
   [...]
   </teiHeader>
   <body>
       <text>
           <div>
                <list rendition="#list1" type="ordered">
                    <item>item 1</item>
                    <item>item 2</item>
                    <item>item 3</item>
                </list>
                <list rendition="#list2" type="ordered">
                    <item>item 1</item>
                    <item>item 2</item>
                    <item>item 3</item>
                </list>
                <list rendition="#list3" type="ordered">
                    <item>item 1</item>
                    <item>item 2</item>
                    <item>item 3</item>
                </list>
                <list rendition="#list4" type="ordered">
                    <item>item 1</item>
                    <item>item 2</item>
                    <item>item 3</item>
                </list>
           </div>
   [...]

*Résultat HTML* :

.. code:: html

   <ol style="list-style-type:upper-roman;" class="texte">    
       <li>item 1</li>    
       <li>item 2</li>    
       <li>item 3</li>
   </ol>
   <ol style="list-style-type:lower-roman;" class="texte">    
       <li>item 1</li>    
       <li>item 2</li>    
       <li>item 3</li>
   </ol>
   <ol style="list-style-type:lower-alpha;" class="texte">    
       <li>item 1</li>    
       <li>item 2</li>    
       <li>item 3</li>
   </ol>
   <ol style="list-style-type:upper-alpha;" class="texte">    
       <li>item 1</li>    
       <li>item 2</li>    
       <li>item 3</li>    
   </ol>   

Tableaux
~~~~~~~~

Les tableaux doivent être décrits à l'aide des balises ``<table>``,
``<row>`` et ``<cell>``. Les attributs rows et cols permettent la fusion
de cellules.

*Xpath* :

-  ``//tei:table``
-  ``//tei:row``
-  ``//tei:cell[@rows and @cols]``

*Exemple* :

.. code:: xml

   [...]
   <table>
       <row>
           <cell rows="2">
               <s>Lots</s>
           </cell>
           <cell rows="2">
               <s>Données 1</s>
           </cell>
           <cell rows="2">
               <s>Données 2</s>
           </cell>
           <cell cols="2">
               <s>Total</s>
           </cell>
       </row>
       <row>
           <cell>
               <s>
                   Total 1<hi rendition="#T12">ère</hi> partie
               </s>
           </cell>
           <cell>
               <s>
                   Total 2<hi rendition="#T12">e</hi> partie
               </s>
           </cell>
       </row>
       <!-- <pb/> -->
       <row>
           <cell rows="2">
               <s>
                    1<hi rendition="#T12">er</hi> lot
               </s>
           </cell>
           <cell>
               <s>12 %</s>
           </cell>
           <cell>
               <s>27 %</s>
           </cell>
           <cell>
               <s>91 %</s>
           </cell>
           <cell>
               <s>98 %</s>
           </cell>
       </row>
       <row>
           <cell>
               <s>26 %</s>
           </cell>
           <cell>
               <s>45 %</s>
           </cell>
           <cell>
               <s>97 %</s>
           </cell>
           <cell>
               <s>92 %</s>
           </cell>
       </row>
       <row>
           <cell rows="2">
               <s>
                   2<hi rendition="#T12">nd</hi> lot
               </s>
           </cell>
           <cell>
               <s>24 %</s>
           </cell>
           <cell>
               <s>85 %</s>
           </cell>
           <cell>
               <s>91 %</s>
           </cell>
           <cell>
               <s>94 %</s>
           </cell>
       </row>
       <row>
           <cell>
               <s>54 %</s>
           </cell>
           <cell>
               <s>54 %</s>
           </cell>
           <cell>
               <s>92 %</s>
           </cell>
           <cell>
               <s>92 %</s>
           </cell>
       </row>
   </table>
   [...]

| *Résultat HTML (rendu)* :
|  Lots Données 1 Données 2 Total Total 1ère partie Total 2e partie 1er
  lot 12 % 27 % 91 % 98 % 26 % 45 % 97 % 92 % 2nd lot 24 % 85 % 91 % 94
  % 54 % 54 % 92 % 92 % 

Liens hypertextes
~~~~~~~~~~~~~~~~~

*Xpath* :

-  ``//tei:ref[@target]``

*Exemple* :

.. code:: xml

   [...]
   <ref target="http://www.openedition.org/​">
       OpenEdition : portail de ressources électroniques en sciences humaines et sociales
   </ref>
   [...]

| *Résultat HTML (rendu)* :
| OpenEdition : portail de ressources électroniques en sciences humaines
  et sociales

Illustrations
~~~~~~~~~~~~~

Pour insérer des images dans un document, il faut créer un archive zip
contenant le fichier TEI de l’article à la racine de cette archive et
les illustrations (au format png, jpg ou gif) qui peuvent être placées
dans une arborescence de répertoire dans l’archive zip.

Pour insérer une illustration dans le document, il faut utiliser la
balise en renseignant dans l’attribut url le chemin relatif vers
l’image.

Les titres, légendes et crédits de l’illustration doivent être stylés
dans des paragraphes ayant un attribut rend="figure-title",
rend="figure-legend", rend="figure-license".

En cas d’utilisation du filtre de vignettisation développé par
OpenEdition, il est impératif de respecter l’ordre des paragraphes
suivant :

-  Titre de l’illustration
-  Illustration
-  Légende de l’illustration
-  Crédits de l’illustration

Aucun des ces élements descriptifs (titre, légende, crédit) n’est
obligatoire.

*Exemple* :

.. code:: xml

   [...]
   <p rend="figure-title">Fonctionnement d'Opentext</p>
   <p>
       <figure>
           <graphic url="relative/path/to/image/img-1.jpg" />
       </figure>
   </p>
   <p rend="figure-legend">Schéma réalisé en septembre 2009</p>
   <p rend="figure-license">Surletoit - licence Creative Commons by-nc-sa</p>
   [...]

Formule
~~~~~~~

La balise ``<formula>`` peut contenir des formules inclues dans un
CDATA. Le contenu ne sera pas traité par Lodel et pourra être interprété
par le navigateur (par exemple avec MathJax).

*Xpath* : ``//tei:p/tei:formula``

*Exemple* :

.. code:: xml

   <p>
   <formula notation="latex"><![CDATA[\[\frac{{\partial v}}{{\partial t}} = \frac{K}{{CD}}\left( {\frac{{{\partial ^2}v}}{{\partial {x^2}}} + \frac{{{\partial ^2}v}}{{\partial {y^2}}} + \frac{{{\partial ^2}v}}{{\partial {z^2}}}} \right)\]]]></formula>
   </p>
   <p>Un formule mathématique inline <formula notation="latex"><![CDATA[\(\frac{{{\partial ^2}v}}{{\partial {z^2}}} = 0\)]]></formula>.</p>
   [...]

*Résultat HTML* :

.. code:: html

   <p class="latex">
   \[\frac{{\partial v}}{{\partial t}} = \frac{K}{{CD}}\left( {\frac{{{\partial ^2}v}}{{\partial {x^2}}} + \frac{{{\partial ^2}v}}{{\partial {y^2}}} + \frac{{{\partial ^2}v}}{{\partial {z^2}}}} \right)\]</formula>
   </p>
   <p class="texte">Un formule mathématique inline <span class="latex">\(\frac{{{\partial ^2}v}}{{\partial {z^2}}} = 0\)</span>.</p>
   [...]
   ]]>

Code
~~~~

La balise ``<code>`` peut contenir des instructions de langages de
programmation. Ce code doit être inclut dans un CDATA.

*Xpath* : ``//tei:p/tei:code``

*Exemple* :

.. code:: xml

   <p rend="noindent">
       <code lang="xml">
   <![CDATA[
   [...]
   <ref target="http://www.openedition.org/​">
       OpenEdition : portail de ressources électroniques en sciences humaines et sociales
   </ref>
   [...]
   ]]>
       </code>
   </p>

*Résultat HTML* :

.. code:: html

   <p class="paragraphesansretrait"></p>
   <pre><code class="brush: xml;">[...]
   &lt;ref target="http://www.openedition.org/​"&gt;
   OpenEdition : portail de ressources électroniques en sciences humaines et sociales
   &lt;/ref&gt;
   [...]</code></pre>

Exemples de linguistique
~~~~~~~~~~~~~~~~~~~~~~~~

Des spécifications particulières ont été définies pour permettre la
publications d'exemples de linguistiques qui présentent les
caractéristiques suivantes :

-  définition d'un type d'exemple
-  numérotation de l'exemple
-  possibilité de définir plusieurs lignes pour un exemple
-  possibilité d'aligner verticalement des segments des lignes de
   l'exemple
-  définition d'une référence bibliographique pour l'exemple
-  définition d'une glose, d'une définition pour l'exemple
-  possibilité d'imbriquer des exemples (définition de sous-exemples)

*Xpath* :

-  Exemple avec type (attribut 'type') et numéro (attribut 'n'). La
   valeur de l'attribut 'type' n'est pas imposée mais la recommandation
   est d'utiliser type="example". : ``//tei:quote[@type][@n]``
-  Les lignes sont définies dans des éléments ``<quote>`` :
   ``//tei:quote[@type][@n]/tei:quote``
-  Les segments de chaque ligne à aligner verticalement sont définis
   dans des éléments ``<seg>`` :
   ``//tei:quote[@type][@n]/tei:quote/tei:seg``
-  La référence bibliographique de l'exemple est définie dans un élément
   ``<bibl>`` : ``//tei:quote[@type][@n]/tei:bibl``
-  La glose ou définition associée à l'exemple est définie dans un
   élément ``<gloss>`` : ``//tei:quote[@type][@n]/tei:gloss``

*Exemple simple* :

.. code:: xml

   [...]
   <quote n="01" type="example">
     <quote>
       <seg>vous dites vous êtes allé donner un cours (H4 / I++)</seg>
       <seg>en fait (H3 / I=)</seg>
     </quote>
     <quote>
       <seg>you say you went to give a class</seg>
       <seg>in fact</seg>
     </quote>
      <bibl>My bibliographic reference</bibl>
      <gloss>My definition (cf &lt;gloss&gt; dans la documentation de référence de la TEI)</gloss>
   </quote> 
   [...]

| *Résultat HTML (rendu)* :
| 
|  01
| quand vous dites vous êtes allé donner un cours (H4 / I++)
| en fait (H3 / I=) 
|  
| when you say you went to give a class
| in fact 
|  My bibliographic reference 
|  My definition (cf <gloss> dans la documentation de référence de la
  TEI) 

*Exemples imbriqués (sous-exemples)* :

.. code:: xml

   [...]
   <quote n="1" type="example">
     <quote n="a" type="example">
       <quote>
         <seg>quand vous dites vous êtes allé donner un cours (H4 / I++)</seg>
         <seg>en fait (H3 / I=)</seg>
       </quote>
       <quote>
         <seg>when you say you went to give a class</seg>
         <seg>in fact</seg>
       </quote>
       <bibl>bibliographic reference for example 1a</bibl>
       <gloss>definition for example 1a</gloss>
     </quote> 
     <quote n="b" type="example">
       <quote>
         <seg>c’est e vous avez voulu (H3 / I=)</seg>
         <seg>savoir comment on pouvait se</seg>
       </quote>
       <quote>
         <seg>it’s er you wanted</seg>
         <seg>to know how one could</seg>
       </quote>
       <bibl>bibliographic reference for example 1b</bibl>
       <gloss>definition for example 1b</gloss>
     </quote>
   </quote>
   [...]

| *Résultat HTML (rendu)* :
| 
|  1 
|  a
| quand vous dites vous êtes allé donner un cours (H4 / I++)
| en fait (H3 / I=) 
|  
| when you say you went to give a class
| in fact 
|  bibliographic reference for example 1a 
|  definition for example 1a 
|  
|  b
| c’est e vous avez voulu (H3 / I=)
| savoir comment on pouvait se 
|  
| it’s er you wanted
| to know how one could 
|  bibliographic reference for example 1b 
|  definition for example 1b 

Back
----

Bibliographie
~~~~~~~~~~~~~

La bibliographie se compose avec les balises ``<listBibl>`` et
``<bibl>``. La bibliographie ne peut pas contenir de section ``<div>``,
à la place on utilise des balises ``<listBibl>`` et ``<head>`` pour
placer des intertitres (voir le Xpath). Les balises ``<listBibl>``
peuvent donc être imbriquées en fonction de la structuration des niveaux
de titres dans la bibliographie.

*Xpath* :

-  Section bibliographie :
   ``/tei:TEI/tei:text/tei:back/tei:div[@type='bibliography']/tei:listBibl``
-  Référence bibliographique :
   ``/tei:TEI/tei:text/tei:back/tei:div[@type='bibliography']//tei:listBibl/tei:bibl``
-  Intertitres :
   ``/tei:TEI/tei:text/tei:back/tei:div[@type='bibliography']//tei:listBibl/tei:head[@subtype='leveln']``
   où 'leveln' peut prendre toutes les valeurs comprises entre 'level1'
   et 'level6'.

*Exemple* :

.. code:: xml

   [...]
   <back>
   <div type="bibliography">
       <listBibl>
           <bibl>
               Bennett, Francis et Michael Holdsworth.
               <hi rend="italic" xml:lang="en">Embracing the Digital Age. An Opportunity for Booksellers and the Book Trade</hi>
               . Londres : The Booksellers Association of the United Kingdom &amp; Ireland, 2007.
           </bibl>
           <listBibl>
               <head subtype="level1">Partie 1</head>
               <bibl>
                   Carrérot, Olivier, éd.
                   <hi rend="italic">Qu’est-ce qu’un livre aujourd’hui ? Pages, marges, écrans</hi>
                   . Les Cahiers de la Librairie. Paris : La Découverte, 2009.
               </bibl>
           </listBibl>
   [...]
       </listBibl>
   </div
   [...]

Annexes
~~~~~~~

Les annexes doivent être placées dans une section de type « appendix ».
Cette section peut contenir tous les éléments utilisables dans le
``<body>`` : citation, illustrations...

*Xpath*: ``/tei:TEI/tei:text/tei:back/tei:div[@type='appendix']``

*Exemple*:

.. code:: xml

   <back>
   [...]
       <div type="appendix">
           <div type="div1">
               <head subtype="level1">Vivamus laoreet</head>
               <p>
                   Nullam tincidunt adipiscing enim. 
               </p>
               <div type="div2">
                   <head subtype="level2">Lorem ipsum</head>
                   <p>
                       Aenean commodo ligula eget dolor. 
                   </p>
                   <p rend="figure-title">Fonctionnement d'Opentext</p>
                   <p>
                       <figure>
                           <graphic url="relative/path/to/image/img-1.jpg" />
                       </figure>
                   </p>
                   <p rend="figure-legend">Schéma réalisé en septembre 2009</p>
                   <p rend="figure-license">Surletoit - licence Creative Commons by-nc-sa</p>
                   <p>
                       Quisque rutrum. Aenean imperdiet. Etiam ultricies nisi vel augue. Curabitur ullamcorper ultricies nisi. 
                   </p>
                   <q rend="quotation">
                       Vestibulum purus quam, scelerisque ut, mollis sed, nonummy id, metus. 
                   </q>
                   <p>
                       <hi xml:lang="en">Nunc nonummy metus. </hi>
                       Vestibulum volutpat pretium libero.
                   </p>
               </div>
           </div>
       </div>
   [...]
   </back>

