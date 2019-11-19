.. _tei-en-body:

body
############################################

.. contents:: Summary
   :depth: 2


.. _tei-en-teibody-intertitres:

Structure of the text and section titles
============================================

**Xpath**

| Sections : ``//div``
| Section titles: ``//head[@subtype='leveln']``

**Use recommandations**

- the document text should be structured by sections (``<div>`` tags).
- section titles should be indicated as the first element of the section in a ``<head>`` tag with an attribute of the ``<subtype="leveln">`` where 'leveln' can take all values between 'level1' and 'level6'.

**Example**

.. code-block:: xml

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


.. _tei-en-teibody-notes:   

Footnotes and endnotes
============================================

**Xpath**

| Footnotes: ``//note[@place='foot' and @n]/p``
| Endnotes: ``//note[@place='end'and @n]/p``

**Use recommandations**

- inserted in the text using ``<note>`` tags;
- the attribute 'place' indicates the type of note;
- the attribute 'n' indicates the note number;
- the note content should imperatively be placed in one or several paragraphs.


**Example**

.. code-block:: xml

   [...] 
   Curabitur ullamcorper ultricies nisi<note place="foot" n="4">
       <p>Nulla consequat massa quis enim.</p>
   </note>. Nam eget dui.<note place="end" n="i">
       <p>Etiam rhoncus.</p>
   </note>
   [...]

**HTML result**

.. code-block:: html

   <p class="paragraphesansretrait">
    Curabitur ullamcorper ultricies nisi
    <a class="footnotecall" id="bodyftn1" href="#ftn1">4</a>
    . Nam eget dui.
    <a class="endnotecall" id="bodyftn2" href="#ftn2">i</a>
  </p>


.. _tei-en-teibody-mises-en-forme:

Text layout: hi tags, rend and rendition attributes
=======================================================

**XPath**

| Text layout : ``//hi[@rend ou @rendition]``
| Format style  : ``/TEI/teiHeader/encodingDesc/tagsDecl``

**Use recommandations**

- allowed values for the attribute 'rend' of the ``<hi>`` tag: ``italic``, ``bold``, ``sup``, ``sub``, ``uppercase``, ``small-caps``, ``underline``;
- the attribute 'rendition' of the ``<hi>`` tag should refer to a css format style defined in ``<tagsDecl>`` in the header.

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

**HTML rendering**

.. raw:: html

   <p class="paragraphesansretrait"><em>Aenean <sup>commodo</sup></em> ligula eget dolor. Aenean massa. <em><strong>Cum sociis</strong></em>                           natoque <em><span style="text-decoration:underline;">penatibus et magnis</span></em>                            dis <em><strong><span style="text-decoration:underline;">parturient montes</span></strong></em>, nascetur <strong><span style="text-decoration:underline;">ridiculus mus</span></strong>.</p>

.. _tei-en-teibody-citations:

Quotation 
===================================

**Xpath**

| Citation: ``//q[@rend='quotation']``
| Citation bis: ``//q[@rend='quotation2']``
| Citation ter: ``//q[@rend='quotation3']``

**Use recommandations**

- use preferably ``<q rend='citation'>``;
- the two others style can be used to differentiate several levels of citation in the html display.

**Example**

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

**HTML result**

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


   
.. _tei-en-teibody-paragraphes:


Paragraph styles
======================================

**Xpath**

| Question: ``//p[@rend='question']``
| Answer: ``//p[@rend='answer']``
| Paragraph without indentation: ``//p[@rend='noindent']``
| Box: ``//p[@rend='box']``
| Epigraph: ``//p[@rend='epigraph']``
| Break: ``//p[@rend='break']``

**Use recommandations**

- Question / Answer styles allow to differentiate these elements in the html display in interviews;
- paragraph without indentation are used to follow the idea, it does not include paragraph numbering.

**Example**

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

**HTML result**

.. code-block:: html

   <p class="question">Question : Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus condimentum accumsan quam, non hendrerit lacus posuere vel.</p>
   <p class="reponse">Réponse : Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus condimentum accumsan quam, non hendrerit lacus posuere vel.  </p>
   <p class="paragraphesansretrait">Paragraphe sans retrait : Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus condimentum accumsan quam, non hendrerit lacus posuere vel. </p>
   <p class="encadre">Encadré : Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus condimentum accumsan quam, non hendrerit lacus posuere vel. </p>
   <p class="epigraphe">              <em>En se réveillant un matin après des rêves agités, Gregor Samsa se retrouva, dans son lit, métamorphosé en un monstrueux insecte.</em>               <br />               Franz Kafka,              <em>La métamorphose</em>            </p> 
   <p rend="separateur">* * *</p> 


.. _tei-en-teibody-listes:


Lists
============================================


**Xpath**

| Elements of non-ordered list: ``//list[@type='unordered']/item``
| Elements of ordered list: ``//list[@type='ordered']/item``

**Use recommandations**

- possibility to nest elements of non-ordered and ordered list;
- possibility to define a numbering type with the attribute 'rendition' of ``<list>`` tag.
- the attribute 'rendition' of ``<list>`` tag refers to a style defined in ``<tagsDecl>`` tag.

Allowed values of the attribute 'rendition' for non-ordered lists :

-  ``list-style-type:disc``
-  ``list-style-type:square``
-  ``list-style-type:circle``

For ordered lists :

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

**HTML result**

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


**Example**

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

**HTML Result**

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



.. _tei-en-teibody-tableaux:   

Tables
============================================

**Xpath**

| Table: ``//table``
| Row: ``//row``
| Cell: ``//cell[@rows and @cols]``


**Use recommandations**

- the attributes 'rows' and 'cols' of ``<cell>`` tag enable fusion of cells.


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

**HTML rendering**

.. raw:: html

  <table>
  <tr><td rowspan="2"><p>Lots</p></td><td rowspan="2"><p>Données 1</p></td><td rowspan="2"><p>Données 2</p></td><td colspan="2"><p>Total</p></td></tr>
  <tr><td><p>Total 1<sup>ère</sup> partie</p></td><td><p>Total 2<sup>e</sup> partie</p></td></tr>
  <tr><td rowspan="2"><p> 1<sup>er</sup> lot</p></td><td><p>12 %</p></td><td><p>27 %</p></td><td><p>91 %</p></td><td><p>98 %</p></td></tr>
  <tr><td><p>26 %</p></td><td><p>45 %</p></td><td><p>97 %</p></td><td><p>92 %</p></td></tr>
  <tr><td rowspan="2"><p>2<sup>nd</sup> lot</p></td><td><p>24 %</p></td><td><p>85 %</p></td><td><p>91 %</p></td><td><p>94 %</p></td></tr>
  <tr><td><p>54 %</p></td><td><p>54 %</p></td><td><p>92 %</p></td><td><p>92 %</p></td></tr>
  </table>


.. _tei-en-teibody-liens: 

Hypertext links
============================================


**Xpath**

| Links: ``//ref[@target]``

**Use recommandations**

- indicate url in the attribute 'target', with protocol (http, https)

**Exemple**

.. code-block:: xml

   [...]
   <ref target="http://www.openedition.org/​">
       OpenEdition : portail de ressources électroniques en sciences humaines et sociales
   </ref>
   [...]

**HTML rendering**

.. raw:: html

  <p><a href="http://www.openedition.org/">OpenEdition : portail de ressources électroniques en sciences humaines et sociales</a></p>


.. _tei-en-teibody-illustrations: 

Images
============================================

**Xpath**

| Image title: ``//p[@rend='figure-title']``
| Image: ``//figure[@url]``
| Image caption: ``//p[@rend='figure-legend']``
| Image credits: ``//p[@rend='figure-license']``

**Use recommandations**

- respect the order of the elements: image title, image, image caption, image credits;
- create a zip archive containing the TEI file of the article at the root of the archive and the illustrations which can be placed in a directory arborescence;
- indicate the path for the image in the 'url' attribute of ``<figure>`` tag;
- images must be in png, jpg, svg or gif format.

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


.. _tei-en-teibody-formule: 

Formula
============================================


**Xpath**

| Formula: ``//p/formula``


**Use recommandations**

- the ``<formula>`` tag can contain math formula. This formula should be included in a CDATA;
- in some websites, the browser can interpret the LaTeX with MathJax to display the formulas.

**Exemple**

.. code-block:: xml

   <p>
   <formula notation="latex"><![CDATA[\[\frac{{\partial v}}{{\partial t}} = \frac{K}{{CD}}\left( {\frac{{{\partial ^2}v}}{{\partial {x^2}}} + \frac{{{\partial ^2}v}}{{\partial {y^2}}} + \frac{{{\partial ^2}v}}{{\partial {z^2}}}} \right)\]]]></formula>
   </p>
   <p>Inline math formula: <formula notation="latex"><![CDATA[\(\frac{{{\partial ^2}v}}{{\partial {z^2}}} = 0\)]]></formula>.</p>
   [...]

**Résultat HTML**

.. code-block:: html

   <p class="latex">
   \[\frac{{\partial v}}{{\partial t}} = \frac{K}{{CD}}\left( {\frac{{{\partial ^2}v}}{{\partial {x^2}}} + \frac{{{\partial ^2}v}}{{\partial {y^2}}} + \frac{{{\partial ^2}v}}{{\partial {z^2}}}} \right)\]</formula>
   </p>
   <p class="texte">Inline math formula: <span class="latex">\(\frac{{{\partial ^2}v}}{{\partial {z^2}}} = 0\)</span>.</p>
   [...]
   ]]>


.. _tei-en-teibody-code:    

Code
============================================


**Xpath**

| Code: ``//p/code``


**Use recommandations**

- indicate programming langage in the attribute 'lang';
- the code should be included in a CDATA.


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

**HTML result**

.. code-block:: html

   <p class="paragraphesansretrait"></p>
   <pre><code class="brush: xml;">[...]
   &lt;ref target="http://www.openedition.org/​"&gt;
   OpenEdition : portail de ressources électroniques en sciences humaines et sociales
   &lt;/ref&gt;
   [...]</code></pre>


.. _tei-en-teibody-linguistique:

Linguistic examples
============================================

**Xpath**

| Examples: ``//quote[@type][@n]``
| Lines: ``//quote[@type][@n]/quote``
| Segments: ``//quote[@type][@n]/quote/seg``
| Bibliographic reference: ``//quote[@type][@n]/bibl``
| Gloss : ``//quote[@type][@n]/gloss``


**Use recommandations**

-  possibility to define a type for the example with the attribute 'type', the recommandation is to use type="example";
-  possibility to number the example with the attribute 'n';
-  possibility to define multiple lines for an example with elements ``<quote>``;
-  possibility to align vertically segments in the lines with elements ``<seg>``;
-  possibility to define bibliographic reference with elements ``<bibl>``;
-  possibility to associate gloss or definition for the example with elements ``<gloss>``;
-  nested examples (definition of sub-examples)


**Simple example**

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

**HTML rendering**

.. raw:: html

  <table><tr><td>01</td><td>quand vous dites vous êtes allé donner un cours (H4 / I++)</td><td>en fait (H3 / I=)</td></tr>
  <tr><td></td><td>when you say you went to give a class</td><td>in fact</td></tr>
  <tr><td></td><td colspan="2">My bibliographic reference</td></tr>
  <tr><td></td><td colspan="2">My definition (cf &lt;gloss&gt; dans la documentation de référence de la TEI)</td></tr>
  </table>
  <br />

**Nested Examples**

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

**HTML rendering**

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