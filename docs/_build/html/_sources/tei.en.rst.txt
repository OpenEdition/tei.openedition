.. _tei-en:

Guidelines (english)
##############################################

| These instructions look at XML markup for documents due to be imported
  into Lodel 1.0. The Xpaths suggested here feature in OpenEdition’s
  editorial model.
| TEI XML schema: http://lodel.org/ns/.
| TEI document example:
  `Lorem-ipsum-Lodel1.0.xml <https://github.com/OpenEdition/tei.openedition/blob/master/doc/lorem_ipsum_lodel_1.0.xml>`__.

**Errata**

Revision 04/27/2015: correction for epigraphs: unlike what was written
in this documentation before this day, epigraphs must be included in the
``<body>`` element, not in the ``<front>`` element.

Revision 04/28/2015: specifications for linguistic examples added.

Revision 10/23/2015: specifications for ``<persName>`` added.

Revision 12/12/2016: list style type

Revision 14/12/2016: fix ``<hi rend="small-caps">``

Revision 03/01/2017: specifications for ``//tei:p[@rend='break']``

Revision 06/01/2017: 2 contributors : collaborator and
excavationsdirector, person cited, math formula

Révision 11/10/2017 : correction on math formula examples

**Outline**

-  `I. teiHeader <#teiheader>`__

   -  `Title, subtitle, suptitle, translated
      titles <#title-subtitle-suptitle-translated-titles>`__
   -  `Authors, translators, scientific editors, excavation director,
      collaborator <#authors-translators-academic-editor-excavation-director-collaborator-archeology-and-their-description>`__
   -  `Using the name tag <#using-the-name-tag>`__
   -  `Using the persName tag <#using-the-name-persname-tag>`__
   -  `Contributors <#contributor-description>`__
   -  `Index : keywords ; geography ; chronology ; themes; person
      cited <#index-keywords-geography-chronology-themes-person-cited>`__
   -  `Publication dates <#print-and-electronic-publication-dates>`__
   -  `Embargo
      periods <#electronic-publication-dates-and-embargo-periods>`__
   -  `Other metadata <#other-metadata>`__

-  `II. text <#text>`__

   -  `II.1. front <#front>`__

      -  `Summaries <#summaries>`__
      -  `Lecture notes <#reading-notes-and-reviews>`__
      -  `Author notes, editors notes, errata,
         acknowledgements <#author-notes-editors-notes-errata-acknowledgements>`__

   -  `II.2. body <#body>`__

      -  `Structure of the text and section
         titles <#structure-of-the-text-and-section-titles>`__
      -  `Footnotes and endnotes <#footnotes-and-endnotes>`__
      -  `Text layout: hi tags, rend and rendition
         attributes <#text-layout-hi-tags-rend-and-rendition-attributes>`__
      -  `Quotations and paragraph
         styles <https://github.com/OpenEdition/lodel/wiki/Creating-a-TEI-document-in-Lodel-1.0#quotation-and-paragraph-styles>`__
      -  `Lists <#lists>`__
      -  `Tables <#tables>`__
      -  `Hypertext links <#hypertext-links>`__
      -  `Images <#images>`__
      -  `Code <#code>`__
      -  `Formula <#formula>`__
      -  `Linguistic examples <#linguistic-examples>`__

   -  `II.3. Back <#back>`__

      -  `Bibliography <#bibliography>`__
      -  `Annexes <#annexes>`__

teiHeader
=========

title, subtitle, suptitle, translated titles
--------------------------------------------

Make sure that each title:

-  Is a single paragraph, without line break (lb tag);
-  Is in lower case, except the first letter;
-  Does not finish with a fullstop.

*Xpath*:

-  Title:
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:title[@type='main']``
-  Subtitle:
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:title[@type='sub']``
-  Suptitle:
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:title[@type='sup']``
-  Translated title:
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:title[@type='alt' and @xml:lang]``
   ``xml:lang`` attribute is required (ISO 639-1).

*Example*:

.. code:: xml

   [...]
   <teiHeader>
       <fileDesc>
         <titleStmt>
           <title type="sup">Dolor sit amet</title>
           <title type="main">Lorem ipsum pour Opentext</title>
           <title type="sub">Basé sur le modèle éditorial pour Lodel de OpenEdition</title>
           <title type="alt" xml:lang="en">Other travelling salesmen live a life of luxury</title>
           <title type="alt" xml:lang="es">Las preocupaciones son mucho mayores</title>
   [...]

authors, translators, academic editor, excavation director, collaborator (archeology) and their description
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

You can associate several authors, translators and editors to the
document.

2 possible encodings for person names : ``<name>`` ou ``<persName>``

Using the name tag
~~~~~~~~~~~~~~~~~~

Make sure both first names and surnames are displayed in this order and
in small case, apart from the first letter. This order is important as
Lodel detects the first name as the first word and the surname as the
second when the document is imported. In the case of a composite
surname, non-breaking spaces
(`http://en.wikipedia.org/​wiki/​Non-breaking_space <http://en.wikipedia.org/​wiki/​Non-breaking_space>`__)
should be used between the different parts of the composite surname to
help Lodel correctly distinguish first names and surnames. Non-breaking
spaces are not necessary for composite first names.

You must always use the same form for author names. Pay special
attention to the case and spelling of first names. E.g. If two documents
from the same author are imported into Lodel, and the author is spelled
John-Arthur Smith in the first and John Arthur Smith, without the
hyphen, in the second, Lodel will consider them as two different authors
and will create separate entries in the author index.

*Xpath*:

-  Author:
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:author/tei:name``
-  Translator:
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:editor[@role='translator']/tei:name``
-  Editor:
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:editor[not(@role)]/tei:name``
-  Excavation director:
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:editor[@role='excavationsdirector']/tei:name``
-  Collaborator (for archeology):
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:editor[@role='collaborator']/tei:name``

Using the name PersName tag
~~~~~~~~~~~~~~~~~~~~~~~~~~~

*Xpath*:

-  Author:
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:author/tei:persName/tei:forename``
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:author/tei:persName/tei:surname``

-  Translator:
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:editor[@role='translator']/tei:persName/tei:forename``
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:editor[@role='translator']/tei:persName/tei:surname``

-  Editor:
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:editor[not(@role)]/tei:persName/tei:forename``
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:editor[not(@role)]/tei:persName/tei:surname``

-  Excavation director (forename and surame):
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:editor[@role='excavationsdirector']/tei:persName/tei:forename``
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:editor[@role='excavationsdirector']/tei:persName/tei:surname``

-  Collaborator (for archeology) (forename and surame):
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:editor[@role='collaborator']/tei:persName/tei:forename``
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:editor[@role='collaborator']/tei:persName/tei:surname``

Contributor description
~~~~~~~~~~~~~~~~~~~~~~~

For each contributor, you can also provide a description using the
``<affiliation>`` tag. You can also use other tags to indicate a
contributor’s affiliation, position, email address, title and web site.

*Xpath*:

-  Author descriptions:
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:author/tei:affiliation/tei:s | /tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:editor/tei:affiliation/tei:s``
-  Affiliation:
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:author/tei:orgName/tei:s | /tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:editor/tei:orgName/tei:s``
-  Position:
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:author/tei:roleName[@type='function']/tei:s | /tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:editor/tei:roleName[@type='function']/tei:s``
-  Title:
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:author/tei:roleName[@type='honorific']/tei:s | /tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:editor/tei:roleName[@type='honorific']/tei:s``
-  Email:
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:author/tei:email/tei:s | /tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:editor/tei:email/tei:s``
-  Web site:
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:author/tei:ref | /tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:editor/tei:ref``

*Example*:

.. code:: xml

   [...]
   <titleStmt>
   [...]
       <author>
           <name>Marin Dacos</name>
           <affiliation>
               Directeur du Cléo (Centre pour l'édition électronique ouverte)
           </affiliation>
           <roleName type="function">
               <s>Directeur</s>
           </roleName>
           <orgName>
               <s>Cléo</s>
           </orgName>
           <email>
               <s>contact@openedition.org</s>
           </email>
           <ref target="http://www.openedition.org" type="website">http://www.openedition.org</​ref>
           <roleName type="honorific">
               <s>M.</s>
           </roleName>
       </author>
       <editor role="translator">
           <persName>
               <forename>Jean-François</forename>
               <surname>Rivière</surname>
           </persName>
           <affiliation>Chargé d'édition au Cléo</affiliation>
       </editor>
       <editor>
           <persName>
               <forename>Nahuel</forename>
               <surname>Angelinetti</surname>
           </persName>
           <affiliation>Développeur au Cléo</affiliation>
       </editor>
   </titleStmt>
   [...]

Index: keywords; geography; chronology; themes; person cited
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

As for author names, spelling and the case used in index entries should
always be the same in order to avoid any duplicates in the index.

For person cited, ``<name>`` ou ``<persname>`` can be used (see author
section for details).

*Xpath*:

-  Keywords:
   ``/tei:TEI/tei:teiHeader/tei:profileDesc/tei:textClass/tei:keywords[@scheme='keyword' and xml:lang]/tei:list/tei:item``.
   ``xml:lang``\ attribute is required (ISO 639-1).

-  Geographical index:
   ``/tei:TEI/tei:teiHeader/tei:profileDesc/tei:textClass/tei:keywords[@scheme='geographical']/tei:list/tei:item``

-  Chronological index:
   ``/tei:TEI/tei:teiHeader/tei:profileDesc/tei:textClass/tei:keywords[@scheme='chronological']/tei:list/tei:item``

-  Thematic index:
   ``/tei:TEI/tei:teiHeader/tei:profileDesc/tei:textClass/tei:keywords[@scheme='subject']/tei:list/tei:item``

-  Person Cited

Using the tag ``<name>`` :
``/tei:TEI/tei:teiHeader/tei:profileDesc/tei:textClass/tei:keywords[@scheme='personcited']/tei:list/tei:item/tei:name``

Using the tag ``<persName>``:
``/tei:TEI/tei:teiHeader/tei:profileDesc/tei:textClass/tei:keywords[@scheme='personcited']/tei:list/tei:item/tei:persName/tei:forename``
``/tei:TEI/tei:teiHeader/tei:profileDesc/tei:textClass/tei:keywords[@scheme='personcited']/tei:list/tei:item/tei:persName/tei:surname``

*Example*:

.. code:: xml

   <profileDesc>
   [...]
       <textClass>
           <keywords scheme="keyword" xml:lang="fr">
               <list>
                   <item>aenean</item>
                   <item>commodo</item>
                   <item>ligula</item>
                   <item>eget</item>
                   <item>dolor</item>
               </list>
           </keywords>
           <keywords scheme="chronological">
               <list>
                   <item>XXIe siecle</item>
               </list>
           </keywords>
           <keywords scheme="geographical">
               <list>
                   <item>France</item>
                   <item>Ile de France</item>
                   <item>Paris</item>
               </list>
           </keywords>
   [...]

Print and electronic publication dates
--------------------------------------

The publication dates of print and electronic issues of a document
should be distinguished.

If the electronic publication date is not indicated in the document, it
will be automatically set by Lodel during import at the date of import.
If the document is reloaded into Lodel, if the date of electronic
publication is not indicated in the document, it will be automatically
set when the document is reloaded. In order to retain a stable
electronic publication date, in the event the document is reloaded, the
publication date should be indicated in the document imported into
Lodel.

*Xpath*:

-  Electronic publication date:
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:publicationStmt/tei:date``
   with the date in the DD/MM/YYYY format
-  Print publication date:
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:sourceDesc/tei:biblFull/tei:publicationStmt/tei:date``
   with the date in the DD/MM/YYYY format

*Example*:

.. code:: xml

   <fileDesc>
   [...]
       <publicationStmt>
           <date>01/07/2010</date> <!--date de publication électronique-->
   [...]
       </publicationStmt>
       <sourceDesc>
           <biblFull>
               <publicationStmt>
                   <date>01/07/2008</date> <!--date de publication papier-->
               </publicationStmt>
   [...]
           </biblFull>
       </sourceDesc>
   [...]

Electronic publication dates and embargo periods
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

For OpenEdition Journals, journals published with an “embargo period”,
Lodel uses the electronic publication date to manage display of the
article in summary or full-text form. For articles with an electronic
publishing date later than the article’s consultation date, only
metadata will be displayed (title, author, summary, abstract, etc),
while articles with an electronic publication date prior to the
article’s consultation date will be displayed in full text. For a two
year “embargo period”, the electronic publishing date should be set two
years after the print publication date. The article will thus become
available in full-text two years after publication of the print version.

Other metadata
--------------

*Xpath*:

-  Language:
   ``/tei:TEI/tei:teiHeader/tei:profileDesc/tei:langUsage/tei:language``
   with a value in ISO 639-1 format
-  Pagination:
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:sourceDesc/tei:biblFull/tei:publicationStmt/tei:idno[@type='pp']``.
   The print pagination of a document can be set in various ways: in
   Roman numbers or and small capitals (V-XXV), or Arabic numbes (5-25).
   All values are valid. Pagination is indicated without using entering
   p. or pp., as these are generally added automatically.
-  Document number:
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:publicationStmt/tei:idno[@type='documentnumber']``.
   This is editorial information that can be displayed in the layout and
   in the document’s electronic reference. The document number can be
   used, for example, to facilitate the citation of electronic
   documents.
-  Licence:
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:publicationStmt/tei:availability``
-  Bibliographical notice for the document:
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:sourceDesc/tei:biblFull/tei:notesStmt/tei:note[@type='bibl']``.
   Here you can note the bibliographical reference of the document’s
   print edition

*Example*:

.. code:: xml

   <fileDesc>
   [...]
       <publicationStmt>
           <date>01/07/2010</date>
           <availability>
               Creative Commons Attribution-NoDerivs 3.0 Unported License
           </availability>
           <idno type="documentnumber">25</idno>
       </publicationStmt>
       <sourceDesc>
           <biblFull>
               <publicationStmt>
                   <date>01/07/2008</date>
                   <idno type="pp">10-27</idno>
               </publicationStmt>
               <notesStmt>
                   <note type="bibl">Référence bibliographique de l'édition papier de cet article.</note>
               </notesStmt>
           </biblFull>
       </sourceDesc>
   </fileDesc>
   [...]
   <profileDesc>
       <langUsage>
           <language>fr</language>
       </langUsage>
   [...]

text
====

front
-----

Summaries
~~~~~~~~~

*Xpath*:

-  Summaries:
   ``/tei:TEI/tei:text/tei:front/tei:div[@type='abstract' and @xml:lang]``
   As for translated titles, the ``xml:lang`` attribute is required with
   a value in ISO 639-1 format.

*Example*:

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

Reading notes and reviews
~~~~~~~~~~~~~~~~~~~~~~~~~

Reading notes and reviews should be styled separately, in separate
files. They should not be entitled “Reading notes”.

If the entry does not have its own distinct title, the “Title” style is
applied to author and title of the reviewed work. It is also possible to
style bibliographical elements (publisher, place and year of
publishing…) as a “subtitle”; this means the bibliographical notice also
features in the summary.

The title, author name, bibliographical notice and date of publication
of reviewed works can also be styled as descriptive elements of the
document.

This information allows for better referencing and offers the
possibility to create specific indexes (an index of authors of reviewed
works for example). This information may be displayed in the layout.

The document should also be given a title, even if the title is the same
as content featuring in the “reviewed work” styles.

*Xpath*:

-  Title of the reviewed work:
   ``/tei:TEI/tei:text/tei:front/tei:div[@type='review']/tei:p[@rend='review-title']``
-  Author of the reviewed work:
   ``/tei:TEI/tei:text/tei:front/tei:div[@type='review']/tei:p[@rend='review-author']``
-  Bibliographical notice of the reviewed work:
   ``/tei:TEI/tei:text/tei:front/tei:div[@type='review']/tei:p[@rend='review-bibliography']``
-  Publication date of the reviewed work:
   ``/tei:TEI/tei:text/tei:front/tei:div[@type='review']/tei:p[@rend='review-date']``

*Example*:

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

Author notes, editors notes, errata, acknowledgements
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

*Xpath*:

-  Author notes:
   ``/tei:TEI/tei:text/tei:front/tei:note[@resp='author']/tei:p``
-  Editor notes:
   ``/tei:TEI/tei:text/tei:front/tei:note[@resp='editor']/tei:p``
-  Erratum:
   ``/tei:TEI/tei:text/tei:front/tei:div[@type='correction']/tei:p``
-  Dedications:
   ``/tei:TEI/tei:text/tei:front/tei:div[@type='dedication']/tei:p``
-  Acknowledgements:
   ``/tei:TEI/tei:text/tei:front/tei:div[@type='ack']/tei:p``

*Example*:

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

BODY
----

Structure of the text and section titles
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The document text should be structured by sections (div tags).

Section titles should be indicated as the first element of the section
in a head tag with an attribute of the subtype="level1" form

*Example*:

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

Footnotes and endnotes
~~~~~~~~~~~~~~~~~~~~~~

Footnotes and endnotes should be inserted in the text using note tags
with a place attribute to indicate the type of note and an n attribute
to indicate the note number. The note content should imperatively be
placed in one or several paragraphs.

*Xpath*:

-  Footnotes: ``//tei:note[@place='foot' and @n]/tei:p``
-  Endnotes: ``//tei:note[@place='end'and @n]/tei:p``

*Example*:

.. code:: xml

   [...] 
   Curabitur ullamcorper ultricies nisi<note place="foot" n="4">
       <p>Nulla consequat massa quis enim.</p>
   </note>. Nam eget dui.<note place="end" n="i">
       <p>Etiam rhoncus.</p>
   </note>
   [...]

*HTML result*:

.. code:: html

   <p class="paragraphesansretrait">Curabitur ullamcorper ultricies nisi<a class="footnotecall" id="bodyftn1" href="#ftn1">4</a>. Nam eget dui.<a class="endnotecall" id="bodyftn2" href="#ftn2">i</a></p>

Text layout: hi tags, rend and rendition attributes
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To apply text layouts, you can use the ``<hi>`` tag with a rend
attribute with the following value: italic, bold, sup, sub, uppercase,
small-caps, underline.

You can also use the ``<hi>`` tag with a rendition attribute referring
to a defined css format style in the header
(``/tei:TEI/tei:teiHeader/tei:encodingDesc/tei:tagsDecl``)

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

*HTML rendering* :

.. raw:: html

   <p class="paragraphesansretrait"><em>Aenean <sup>commodo</sup></em> ligula eget dolor. Aenean massa. <em><strong>Cum sociis</strong></em>                           natoque <em><span style="text-decoration:underline;">penatibus et magnis</span></em>                            dis <em><strong><span style="text-decoration:underline;">parturient montes</span></strong></em>, nascetur <strong><span style="text-decoration:underline;">ridiculus mus</span></strong>.</p>

Quotation and paragraph styles
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The following internal styles are declared in the editorial model.
*Xpath*:

-  Citation: ``//tei:q[@rend='quotation']``
-  Citation bis: ``//tei:q[@rend='quotation2']``
-  Citation ter: ``//tei:q[@rend='quotation3']``
-  Question: ``//tei:p[@rend='question']``
-  Answer: ``//tei:p[@rend='answer']``
-  Paragraphe without indentation: ``//tei:p[@rend='noindent']``
-  Box: ``//tei:p[@rend='box']``
-  Epigraph: ``//tei:p[@rend='epigraph']``
-  Break: ``//tei:p[@rend='break']``

*Example*:

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

*HTML result* :

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
   <p rend="separateur">* * *</p> 

Lists
~~~~~

Ordered or non-ordered lists are possible and can be interlinked.

*Xpath* :

-  Elements of non-ordered list:
   ``//tei:list[@type='unordered']/tei:item``
-  Elements of ordered list: ``//tei:list[@type='ordered']/tei:item``

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

*HTML result* :

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

List style types
^^^^^^^^^^^^^^^^

List style type can be definied using ``rendition`` attribut of
``<list>`` element.

Allowed values for non-ordered lists :

-  ``list-style-type:disc``
-  ``list-style-type:square``
-  ``list-style-type:circle``

Allowed values for ordered lists :

-  ``list-style-type:decimal``
-  ``list-style-type:lower-roman``
-  ``list-style-type:upper-roman``
-  ``list-style-type:lower-alpha``
-  ``list-style-type:upper-alpha``

*Example* :

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

*HTML Result* :

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

Tables
~~~~~~

Tables should be formatted using ``<table>``, ``<row>`` and ``<cell>``
tags. The attributes rows and cols enable fusion of cells.

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

| *HTML rendering* :
|  Lots Données 1 Données 2 Total Total 1ère partie Total 2e partie 1er
  lot 12 % 27 % 91 % 98 % 26 % 45 % 97 % 92 % 2nd lot 24 % 85 % 91 % 94
  % 54 % 54 % 92 % 92 % 

Hypertext links
~~~~~~~~~~~~~~~

*Xpath*:

-  ``//tei:ref[@target]``

*Exemple* :

.. code:: xml

   [...]
   <ref target="http://www.openedition.org/​">
       OpenEdition : portail de ressources électroniques en sciences humaines et sociales
   </ref>
   [...]

| *HTML rendering* :
| OpenEdition : portail de ressources électroniques en sciences humaines
  et sociales

Images
~~~~~~

To insert images in a document, you should create a zip archive
containing the TEI file of the article at the root of the archive and
the illustrations (in png, jpg or gif format) which can be placed in a
directory arborescence in the zip archive.

To insert an illustration in the document, use the tag and indicate the
path for the image in theurl attribute.

Titles, captions and credits for the image should be styled in the
paragraphs with a rend="figure-title",rend="figure-legend" or
rend="figure-license" attribute.

If you are using the thumbnail filter developed by OpenEdition, you must
respect the following paragraph order:

-  Image title
-  Image
-  Image caption
-  Image credits

None of the descriptive elements (title, caption, credits) are required.

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

Formula
~~~~~~~

The ``<formula>`` tag can contain math formula. This formula should be
included in a CDATA.

*Xpath* : ``//tei:p/tei:formula``

*Exemple* :

.. code:: xml

   <p>
   <formula notation="latex"><![CDATA[\[\frac{{\partial v}}{{\partial t}} = \frac{K}{{CD}}\left( {\frac{{{\partial ^2}v}}{{\partial {x^2}}} + \frac{{{\partial ^2}v}}{{\partial {y^2}}} + \frac{{{\partial ^2}v}}{{\partial {z^2}}}} \right)\]]]></formula>
   </p>
   <p>Inline math formula: <formula notation="latex"><![CDATA[\(\frac{{{\partial ^2}v}}{{\partial {z^2}}} = 0\)]]></formula>.</p>
   [...]

*Résultat HTML* :

.. code:: html

   <p class="latex">
   \[\frac{{\partial v}}{{\partial t}} = \frac{K}{{CD}}\left( {\frac{{{\partial ^2}v}}{{\partial {x^2}}} + \frac{{{\partial ^2}v}}{{\partial {y^2}}} + \frac{{{\partial ^2}v}}{{\partial {z^2}}}} \right)\]</formula>
   </p>
   <p class="texte">Inline math formula: <span class="latex">\(\frac{{{\partial ^2}v}}{{\partial {z^2}}} = 0\)</span>.</p>
   [...]
   ]]>

Code
~~~~

The ``<code>`` tag can contain programming language instructions. This
code should be included in a CDATA.

*Xpath* :

::

   `//tei:p/tei:code`

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

*HTML result* :

.. code:: html

   <p class="paragraphesansretrait"></p>
   <pre><code class="brush: xml;">[...]
   &lt;ref target="http://www.openedition.org/​"&gt;
   OpenEdition : portail de ressources électroniques en sciences humaines et sociales
   &lt;/ref&gt;
   [...]</code></pre>

Linguistic examples
~~~~~~~~~~~~~~~~~~~

Specifications have been defined for linguistic examples with the
following caracteristics:

-  definition of a type for the example
-  definition of a number for the example
-  multiple lines for an example
-  vertical align of segments in the lines of the example
-  bibliographic reference for the example
-  gloss or definition for the example
-  nested examples (definition of sub-examples)

*Xpath* :

-  Example with type ('type' attribute) et number ('n' attribute). The
   value of the type attribute is not restricted but the recommandation
   is to use type="example". ``//tei:quote[@type][@n]``
-  Lines are defined in ``<quote>`` elements:
   ``//tei:quote[@type][@n]/tei:quote``
-  Segments of each lines are defined in ``<seg>`` elements:
   ``//tei:quote[@type][@n]/tei:quote/tei:seg``
-  Bibliographic reference for the example is defined in a ``<bibl>``
   element: ``//tei:quote[@type][@n]/tei:bibl``
-  Gloss or definition for the example is defined in a ``<gloss>``
   element: ``//tei:quote[@type][@n]/tei:gloss``

*Simple example* :

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

| *HTML rendering* :
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

| *HTML rendering* :
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

Bibliography
~~~~~~~~~~~~

Bibliographies are created using the ``<listBibl>`` and ``<bibl>`` tags.
The bibliography cannot contain sections ``<div>``, but ``<listBibl>``
and ``<head>`` tags can be used to insert section titles (see the
XPath). The ``<listBibl>`` tags can be nested according to the
structuring of title levels in the bibliography.

*Xpath* :

-  Bibliography section:
   ``/tei:TEI/tei:text/tei:back/tei:div[@type='bibliography']/tei:listBibl``
-  Bibliographical reference:
   ``/tei:TEI/tei:text/tei:back/tei:div[@type='bibliography']//tei:listBibl/tei:bibl``
-  Section titles:
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

Annexes should be placed in an “appendix” type section. The section can
contain all elements applicable in the ``<body>``: quotations,
illustrations, etc.

*Xpath*:

-  ``/tei:TEI/tei:text/tei:back/tei:div[@type='appendix']``

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

