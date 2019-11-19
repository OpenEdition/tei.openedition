.. _tei-fr-body:

body
############################################

.. contents:: Sommaire
   :depth: 2


.. _tei-fr-teibody-intertitres:

Structure du texte et intertitres
============================================

**Xpath**

| sections : ``//div``
| Intertitres : ``//head[@subtype='leveln']``

**Recommandations d'usages**

- le texte du document doit être structuré par des sections (balises ``<div>``) ;
- les intertitres doivent être indiqués comme premier élément de la section dans une balise ``<head>`` avec un attribut ``subtype="leveln"``  où 'leveln' peut prendre toutes les valeurs comprises entre 'level1' et 'level6'

**Exemple**

.. code-block:: xml

   [...]
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


.. _tei-fr-teibody-notes:   

Notes de bas de page et notes de fin
============================================


**Xpath**

| Note de bas de page : ``//note[@place='foot' and @n]/p``
| Note de fin : ``//note[@place='end'and @n]/p``
  

**Recommandations d'usages**

- insérées dans le texte dans des balises ``<note>`` ;
- l'attribut 'place' indique le type de note ;
- l'attribut 'n' indique le numéro de la note ;
- le contenu de la note doit impérativement être placé dans un ou plusieurs paragraphes.


**Exemple**

.. code-block:: xml

   [...]
   Curabitur ullamcorper ultricies nisi<note place="foot" n="4">
       <p>Nulla consequat massa quis enim.</p>
       </note>. Nam eget dui.
       <note place="end" n="i"><p>Etiam rhoncus.</p>
   </note>
   [...]

**Résultat HTML**

.. code-block:: html

   <p class="paragraphesansretrait">
     Curabitur ullamcorper ultricies nisi
     <a class="footnotecall" id="bodyftn1" href="#ftn1">4</a>
     . Nam eget dui.
     <a class="endnotecall" id="bodyftn2" href="#ftn2">i</a>
   </p>

.. _tei-fr-teibody-mises-en-forme:

Mises en forme du texte : balises hi, attributs rend et rendition
======================================================================

**XPath**

| Mise en forme : ``//hi[@rend ou @rendition]``
| Définition des styles  : ``/TEI/teiHeader/encodingDesc/tagsDecl``

**Recommandations d'usages**

- valeurs possibles pour l'attribut 'rend' de la balise ``<hi>`` : ``italic``, ``bold``, ``sup``, ``sub``, ``uppercase``, ``small-caps``, ``underline`` ; 
- l'attribut 'rendition' de la balise ``<hi>`` doit faire référence à un style défini au format css dans la balise ``<tagsDecl>`` du header.

**Exemple**

.. code-block:: xml

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

**Résultat HTML (rendu)**

.. raw:: html

  <p>
    <em>Aenean <sup>commodo</sup></em> ligula eget dolor. Aenean massa. <em><strong>Cum sociis</strong></em> natoque 
    <em><span style="text-decoration:underline;">penatibus et magnis</span></em> dis 
    <em><strong><span style="text-decoration:underline;">parturient montes</span></strong></em>, nascetur 
    <strong><span style="text-decoration:underline;">ridiculus mus</span></strong>.
  </p>

.. _tei-fr-teibody-citations:

Citations 
===================================

**Xpath**

| Citation : ``//q[@rend='quotation']``
| Citation bis : ``//q[@rend='quotation2']``
| Citation ter : ``//q[@rend='quotation3']``

**Recommandations d'usages**

- utiliser de préférence ``<q rend='citation'>`` ;
- les 2 autres styles de citations servent à différencier plusieurs niveaux de citation au niveau de l'affichage html.

**Exemple**

.. code-block:: xml

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
   [...]

**Résultat HTML**

.. code-block:: html

   <blockquote>
    <p class="citation">Citation : Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus condimentum accumsan quam, non hendrerit lacus posuere vel. </p>
   </blockquote>
   <blockquote class="citationbis">
    <p class="citationbis">Citation bis : Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus condimentum accumsan quam, non hendrerit lacus posuere vel. </p>
   </blockquote>
   <blockquote class="citationter">
    <p class="citationter">Citation ter : Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus condimentum accumsan quam, non hendrerit lacus posuere vel.</p>
   </blockquote>


.. _tei-fr-teibody-paragraphes:


Styles de paragraphe (question, réponse, paragraphe sans retrait, encadré, épigraphe)
=============================================================================================

**Xpath**

| Question : ``//p[@rend='question']``
| Réponse : ``//p[@rend='answer']``
| Paragraphe sans retrait : ``//p[@rend='noindent']``
| Encadré : ``//p[@rend='box']``
| Epigraphe : ``//p[@rend='epigraph']``
| Séparateur : ``//p[@rend='break']``

**Recommandations d'usages**

- les styles questions / réponses permettent de différencier ces éléments au niveau de l'affichage html dans les entretiens
- le paragraphe sans retrait est utilisé pour exprimer une continuité d'idée, il ne comporte pas de numérotation de paragraphe

**Exemple**

.. code-block:: xml

   [...]
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

**Résultat HTML**

.. code-block:: html

   <p class="question">Question : Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus condimentum accumsan quam, non hendrerit lacus posuere vel.</p>
   <p class="reponse">Réponse : Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus condimentum accumsan quam, non hendrerit lacus posuere vel.  </p>
   <p class="paragraphesansretrait">Paragraphe sans retrait : Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus condimentum accumsan quam, non hendrerit lacus posuere vel. </p>
   <p class="encadre">Encadré : Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus condimentum accumsan quam, non hendrerit lacus posuere vel. </p>
   <p class="epigraphe">              <em>En se réveillant un matin après des rêves agités, Gregor Samsa se retrouva, dans son lit, métamorphosé en un monstrueux insecte.</em>               <br />               Franz Kafka,              <em>La métamorphose</em>            </p>
   <p class="separateur">* * *</p>   


.. _tei-fr-teibody-listes:


Listes
============================================

**Xpath**

| Éléments de liste non-ordonnée : ``//list[@type='unordered']/item``
| Éléments de liste ordonnée : ``//list[@type='ordered']/item``
  
**Recommandations d'usages**

- possibilité d'imbriquer des éléments de listes ordonnées ou non ordonnées ; 
- possibilité de définir un type de numérotation avec l' attribut 'rendition' sur l'élément ``<list>``. 
- l'attribut 'rendition' fait référence à un style défini dans la balise ``<tagsDecl>`` du header.
  
Valeurs autorisées de l'attribut 'rendition' pour les listes non ordonnées :

-  ``list-style-type:disc``
-  ``list-style-type:square``
-  ``list-style-type:circle``

Pour les listes ordonnées :

-  ``list-style-type:decimal``
-  ``list-style-type:lower-roman``
-  ``list-style-type:upper-roman``
-  ``list-style-type:lower-alpha``
-  ``list-style-type:upper-alpha``  

**Exemple**

.. code-block:: xml

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

**Résultat HTML**

.. code-block:: html

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



**Exemple**

.. code-block:: xml

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

**Résultat HTML**

.. code-block:: html

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

.. _tei-fr-teibody-tableaux:   

Tableaux
============================================

**Xpath**

-  Tableau : ``//table``
-  Ligne : ``//row``
-  Cellule : ``//cell[@rows and @cols]``
   
**Recommandations d'usages**

- les attributs 'rows' et 'cols' des balises ``<cell>`` permettent la fusion de cellules.

**Exemple**

.. code-block:: xml

   [...]
   <table>
       <row>
           <cell rows="2">Lots</cell>
           <cell rows="2">Données 1</cell>
           <cell rows="2">Données 2</cell>
           <cell cols="2">Total</cell>
       </row>
       <row>
           <cell>Total 1<hi rendition="#T12">ère</hi> partie</cell>
           <cell>Total 2<hi rendition="#T12">e</hi> partie</cell>
       </row>
       <row>
           <cell rows="2">1<hi rendition="#T12">er</hi> lot</cell>
           <cell>12 %</cell>
           <cell>27 %</cell>
           <cell>91 %</cell>
           <cell>98 %</cell>
       </row>
       <row>
           <cell>26 %</cell>
           <cell>45 %</cell>
           <cell>97 %</cell>
           <cell>s>92 %</cell>
       </row>
       <row>
           <cell rows="2">2<hi rendition="#T12">nd</hi> lot</cell>
           <cell>24 %</cell>
           <cell>85 %</cell>
           <cell>91 %</cell>
           <cell>94 %</cell>
       </row>
       <row>
           <cell>54 %</cell>
           <cell>54 %</cell>
           <cell>92 %</cell>
           <cell>92 %</cell>
       </row>
   </table>
   [...]


**Résultat HTML (rendu)**

.. raw:: html

  <table>
  <tr><td rowspan="2"><p>Lots</p></td><td rowspan="2"><p>Données 1</p></td><td rowspan="2"><p>Données 2</p></td><td colspan="2"><p>Total</p></td></tr>
  <tr><td><p>Total 1<sup>ère</sup> partie</p></td><td><p>Total 2<sup>e</sup> partie</p></td></tr>
  <tr><td rowspan="2"><p> 1<sup>er</sup> lot</p></td><td><p>12 %</p></td><td><p>27 %</p></td><td><p>91 %</p></td><td><p>98 %</p></td></tr>
  <tr><td><p>26 %</p></td><td><p>45 %</p></td><td><p>97 %</p></td><td><p>92 %</p></td></tr>
  <tr><td rowspan="2"><p>2<sup>nd</sup> lot</p></td><td><p>24 %</p></td><td><p>85 %</p></td><td><p>91 %</p></td><td><p>94 %</p></td></tr>
  <tr><td><p>54 %</p></td><td><p>54 %</p></td><td><p>92 %</p></td><td><p>92 %</p></td></tr>
  </table>


.. _tei-fr-teibody-liens: 

Liens hypertextes
============================================

**Xpath**

Liens : ``//ref[@target]``

**Recommandations d'usages**

- indiquer l'url dans l'attribut target, avec le protocole (http, https, etc.)

**Exemple**

.. code-block:: xml

   [...]
   <ref target="http://www.openedition.org/​">
       OpenEdition : portail de ressources électroniques en sciences humaines et sociales
   </ref>
   [...]

**Résultat HTML (rendu)**

.. raw:: html

  <p><a href="http://www.openedition.org/">OpenEdition : portail de ressources électroniques en sciences humaines et sociales</a></p>

.. _tei-fr-teibody-illustrations: 

Illustrations
============================================

**Xpath**

| Titre de l’illustration : ``//p[@rend='figure-title']``
| Illustration : ``//figure[@url]``
| Légende de l’illustration : ``//p[@rend='figure-legend']``
| Crédits de l’illustration : ``//p[@rend='figure-license']``


**Recommandations d'usages**

- respecter l'ordre des éléments : titre de l'illustration, illustration, légende, crédits ;
- créer une archive zip contenant le fichier TEI du document à la racine et les illustrations qui peuvent être placées dans une arborescence de répertoire ;
- l'attribut 'url' de la balise ``<figure>`` contient le chemin relatif au fichier à l'intérieur de l'archive ;
- les formats autorisés pour les illustrations sont : png, jpg, gif, svg ; 


**Exemple**

.. code-block:: xml

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


.. _tei-fr-teibody-formule: 

Formules
============================================

**Xpath**

Formule : ``//p/formula``

**Recommandations d'usages**

- inclure les formules à l'intérieur de la balise ``<formula>`` dans un CDATA, le contenu ne sera pas traité par Lodel.
- Sur certains sites, le navigateur peut interpréter le LaTeX avec MathJax pour afficher les formules.


**Exemple**

.. code-block:: xml

   <p>
   <formula notation="latex"><![CDATA[\[\frac{{\partial v}}{{\partial t}} = \frac{K}{{CD}}\left( {\frac{{{\partial ^2}v}}{{\partial {x^2}}} + \frac{{{\partial ^2}v}}{{\partial {y^2}}} + \frac{{{\partial ^2}v}}{{\partial {z^2}}}} \right)\]]]></formula>
   </p>
   <p>Un formule mathématique inline <formula notation="latex"><![CDATA[\(\frac{{{\partial ^2}v}}{{\partial {z^2}}} = 0\)]]></formula>.</p>
   [...]

**Résultat HTML**

.. code-block:: html

   <p class="latex">
   \[\frac{{\partial v}}{{\partial t}} = \frac{K}{{CD}}\left( {\frac{{{\partial ^2}v}}{{\partial {x^2}}} + \frac{{{\partial ^2}v}}{{\partial {y^2}}} + \frac{{{\partial ^2}v}}{{\partial {z^2}}}} \right)\]</formula>
   </p>
   <p class="texte">Un formule mathématique inline <span class="latex">\(\frac{{{\partial ^2}v}}{{\partial {z^2}}} = 0\)</span>.</p>
   [...]
   ]]>


.. _tei-fr-teibody-code:    

Code
============================================


**Xpath**

Code : ``//p/code[@lang]``

**Recommandations d'usages**

- préciser le langage de programmation dans l'attribut 'lang' ;
- inclure le code dans un CDATA.

**Exemple**

.. code-block:: xml

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

**Résultat HTML**

.. code-block:: html

   <p class="paragraphesansretrait"></p>
   <pre><code class="brush: xml;">[...]
   &lt;ref target="http://www.openedition.org/​"&gt;
   OpenEdition : portail de ressources électroniques en sciences humaines et sociales
   &lt;/ref&gt;
   [...]</code></pre>


.. _tei-fr-teibody-linguistique:

Exemples de linguistique
============================================

**Xpath**

| Exemple : ``//quote[@type][@n]``
| Lignes : ``//quote[@type][@n]/quote``
| Segments : ``//quote[@type][@n]/quote/seg``
| Référence bibliographique : ``//quote[@type][@n]/bibl``
| Glose : ``//quote[@type][@n]/gloss``


**Recommandations d'usages**   

- possibilité de définir le type d'exemple avec l'attribut 'type' pour la balise ``<quote>`` (type recommandé : "example") ;
- possibilité de numéroter l'exemple avec l'attibut 'n' de la balise ``<quote>`` ;
- possibilité de définir plusieurs lignes d'exemples avec des éléments ``<quote>`` ;
- possibilité d'aligner verticalement des segments des lignes de l'exemple avec des éléments ``<seg>`` ;
- possibilité de définir une référence bibliographique dans un élément ``<bibl>`` ;
- possibilité d'associer une glose ou une définition à l'exemple dans un élément ``<gloss>`` ;
- possibilité d'imbriquer des exemples (définition de sous-exemples).

**Exemple simple**

.. code-block:: xml

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

*Résultat HTML (rendu)**

.. raw:: html

  <table><tr><td>01</td><td>quand vous dites vous êtes allé donner un cours (H4 / I++)</td><td>en fait (H3 / I=)</td></tr>
  <tr><td></td><td>when you say you went to give a class</td><td>in fact</td></tr>
  <tr><td></td><td colspan="2">My bibliographic reference</td></tr>
  <tr><td></td><td colspan="2">My definition (cf &lt;gloss&gt; dans la documentation de référence de la TEI)</td></tr>
  </table>
  <br />



**Exemples imbriqués (sous-exemples)**

.. code-block:: xml

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

**Résultat HTML (rendu)**


.. raw:: html

  <table>
  <tr>
  <td>1</td>
  <td>
  <table>
  <tr>
  <td>a</td>
  <td>quand vous dites vous êtes allé donner un cours (H4 / I++)</td>
  <td>en fait (H3 / I=)</td>                </tr>
  <tr>
  <td> </td>
  <td>when you say you went to give a class</td>
  <td>in fact</td>                </tr>
  <tr>
  <td> </td>
  <td colspan="2">bibliographic reference for example 1a</td>
  </tr>
  <tr>
  <td> </td>
  <td colspan="2">definition for example 1a</td>
  </tr>              </table>
  </td>
  </tr>
  <tr>
  <td> </td>
  <td>
  <table>
  <tr>
  <td>b</td>
  <td>c’est e vous avez voulu (H3 / I=)</td>
  <td>savoir comment on pouvait se</td>                </tr>
  <tr>
  <td> </td>
  <td>it’s er you wanted</td>
  <td>to know how one could</td>                </tr>
  <tr>
  <td> </td>
  <td colspan="2">bibliographic reference for example 1b</td>
  </tr>
  <tr>
  <td> </td>
  <td colspan="2">definition for example 1b</td>
  </tr>              </table>
  </td>
  </tr>            </table>
  <br />