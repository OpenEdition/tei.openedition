.. _tei-fr-teiHeader:


teiHeader
############################################

.. contents:: Sommaire
   :depth: 7



title
============================================

XPath
--------------------------------------------

-  Titre :
   ``xml /tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:title[@type='main']``

-  Sous-titre :
   ``xml /tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:title[@type='sub']``

-  Surtitre :
   ``xml /tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:title[@type='sup']``

-  Titres traduits :
   ``xml /tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:title[@type='alt' and @xml:lang]``

-  Pour les titres traduits, l'attribut ``xml xml:lang`` est obligatoire
   avec un valeur au format ISO 639-1.


Application
--------------------------------------------

- import OpenEdition Journals
- import OpenEdition Books 
- export TEI OpenEdition

Recommandations d'usage
--------------------------------------------

Veiller à ce que chaque titre :

-  constitue un seul paragraphe, sans saut de ligne (balise lb) ;
-  soit affiché en minuscules sauf initiale ;
-  ne soit pas terminé par un point.

Exemple
--------------------------------------------

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








Titre, sous-titre, surtitre, titres traduits
--------------------------------------------
*Xpath*:
*Exemple*:
Auteurs, traducteurs, éditeurs scientifiques, directeurs de fouilles, collaborateurs (pour l'archéologie) et leur description
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Il est bien-sûr possible d'indiquer plusieurs auteurs, traducteurs, etc.
pour le document.

2 possibilités d'encodage pour les noms de personnes : ``<name>`` ou
``<persName>``

Utilisation de la balise name
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Veillez à ce que les prénoms et noms soient affichés dans cet ordre et
en minuscule sauf initiale. Cet ordre est important car Lodel va en
déduire le prénom (premier mot) et le nom (deuxième mot) au moment de
l’importation. En cas de nom composé, il faut utiliser des espaces
insécables
(`http://fr.wikipedia.org/​wiki/​Espace_ins%C3%A9cable <http://fr.wikipedia.org/​wiki/​Espace_ins%C3%A9cable>`__)
entre les différentes parties du nom composé. De cette manière Lodel
distinguera correctement prénoms et noms. Cette recommandation n'est pas
nécessaire pour les prénoms composés.

Il est indispensable d’utiliser toujours la même forme pour les noms
d’auteurs. En particulier, prêter attention à la casse, et à
l’orthographe des prénoms. Ex : Si deux documents d’un même auteur sont
importés dans Lodel , l’auteur étant orthographié Jean-Paul Durand dans
le premier document, et Jean Paul Durand (sans tiret) dans le second,
Lodel les considérera comme deux auteurs différents, et créera deux
entrées distinctes dans l’index des auteurs.

*Xpath* :

-  Auteur :
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:author/tei:name``
-  Traducteur :
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:editor[@role='translator']/tei:name``
-  Éditeur scientifique :
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:editor[not(@role)]/tei:name``
-  Directeur de fouilles :
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:editor[@role='excavationsdirector']/tei:name``
-  Collaborateur (pour l'archéologie) :
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:editor[@role='collaborator']/tei:name``

Utilisation de la balise persName
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

*Xpath* :

-  Auteur (prénom et nom)
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:author/tei:persName/tei:forename``
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:author/tei:persName/tei:surname``
-  Traducteur (prénom et nom)
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:editor[@role='translator']/tei:persName/tei:forename``
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:editor[@role='translator']/tei:persName/tei:surname``
-  Éditeur scientifique (prénom et nom)
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:editor[not(@role)]/tei:persName/tei:forename``
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:editor[not(@role)]/tei:persName/tei:surname``
-  Directeur de fouilles (prénom et nom)
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:editor[@role='excavationsdirector']/tei:persName/tei:forename``
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:editor[@role='excavationsdirector']/tei:persName/tei:surname``
-  Collaborateur (pour l'archéologie) (prénom et nom)
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:editor[@role='collaborator']/tei:persName/tei:forename``
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:editor[@role='collaborator']/tei:persName/tei:surname``

Description des contributeurs
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Pour chacun de ces contributeurs, il est possible de donner une
description. La description générale du contributeur est donnée dans la
balise ``<affiliation>``. Il est également possible d'utiliser d'autres
balises pour préciser l'affiliation, la fonction, le courriel, le
préfixe et le site web.

*Xpath*:

-  Description d'auteur
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:author/tei:affiliation/tei:s | /tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:editor/tei:affiliation/tei:s``
-  Affiliation
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:author/tei:orgName/tei:s | /tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:editor/tei:orgName/tei:s``
-  Fonction
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:author/tei:roleName[@type='function']/tei:s | /tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:editor/tei:roleName[@type='function']/tei:s``
-  Préfixe
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:author/tei:roleName[@type='honorific']/tei:s | /tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:editor/tei:roleName[@type='honorific']/tei:s``
-  Courriel
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:author/tei:email/tei:s | /tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:editor/tei:email/tei:s``
-  Site web
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:author/tei:ref | /tei:TEI/tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:editor/tei:ref``

*Exemple*:

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

.. _index--mots-clés-keywords--géographie--chronologie--thèmes--personnes-citées:

Index : Mots-clés, keywords... ; géographie ; chronologie ; thèmes ; personnes citées
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Comme pour les noms d’auteurs, l’orthographe et la casse des entrées
d’index doivent toujours être les mêmes afin d’éviter les doublons dans
les index.

Pour les personnes citées, on peut utiliser la balise ``<name>`` ou
``<persname>`` (se référer à la sections auteurs pour les précisions).

*Xpath*:

-  Mots-clés, keywords, palabras claves, etc.
   ``/tei:TEI/tei:teiHeader/tei:profileDesc/tei:textClass/tei:keywords[@scheme='keyword' and xml:lang]/tei:list/tei:item``
   Pour les keywords, l'attribut ``xml:lang`` est obligatoire avec un
   valeur au format ISO 639-1.

-  Index géographique
   ``/tei:TEI/tei:teiHeader/tei:profileDesc/tei:textClass/tei:keywords[@scheme='geographical']/tei:list/tei:item``

-  Index chronologique
   ``/tei:TEI/tei:teiHeader/tei:profileDesc/tei:textClass/tei:keywords[@scheme='chronological']/tei:list/tei:item``

-  Index thématique
   ``/tei:TEI/tei:teiHeader/tei:profileDesc/tei:textClass/tei:keywords[@scheme='subject']/tei:list/tei:item``

-  Index des personnes citées utilisation de ``<name>`` :
   ``/tei:TEI/tei:teiHeader/tei:profileDesc/tei:textClass/tei:keywords[@scheme='personcited']/tei:list/tei:item/tei:name``

utilisation de ``<persName>`` :
``/tei:TEI/tei:teiHeader/tei:profileDesc/tei:textClass/tei:keywords[@scheme='personcited']/tei:list/tei:item/tei:persName/tei:forename``
``/tei:TEI/tei:teiHeader/tei:profileDesc/tei:textClass/tei:keywords[@scheme='personcited']/tei:list/tei:item/tei:persName/tei:surname``

*Exemple*:

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
           <keywords scheme="personcited">
             <list>
                 <item>
                     <name>Pierre Durand</name>
                 </item>
                 <item>
                     <persName>
                         <forename>Olivier</forename>
                         <surname>Dumond</surname>
                     </persName>
                 </item>
             </list>
           </keywords>

   [...]

Dates de publication papier et électronique
-------------------------------------------

On distingue la date de publication papier et la date de publication
électronique d’un document.

Si la date de publication électronique n’est pas indiquée dans le
document, elle sera automatiquement renseignée par Lodel lors de
l’importation du document et fixée au jour de l’importation du document.
En cas de rechargement du document dans Lodel, si la date de publication
électronique n’est pas indiquée dans le document elle sera fixée
automatiquement au jour du rechargement du document. Afin de conserver
une date de publication électronique stable, même en cas de rechargement
du document, il est donc nécessaire de l’indiquer dans le document
importé dans Lodel.

*Xpath*:

-  Date de publication électronique :
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:publicationStmt/tei:date``
   avec une date au format : JJ/MM/AAAA
-  Date de publication papier :
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:sourceDesc/tei:biblFull/tei:publicationStmt/tei:date``
   avec une date au format : JJ/MM/AAAA

*Exemple*:

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

Date de publication électronique et barrière mobile
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Pour les revues adhérant à OpenEdition Journals et utilisant la fonction
de « barrière mobile », la date de publication électronique sera
utilisée par Lodel pour gérer l’affichage de l’article sous forme de
résumé ou en texte intégral. Pour les articles ayant une date de
publication électronique postérieure à la date de consultation de
l’article, seules les métadonnées seront affichées (titre, auteur,
résumés, abstract…) ; pour les articles ayant une date de publication
électronique antérieure à la date de consultation de l’article seront
affichés en texte intégral. Pour une « barrière mobile » de deux ans, la
date de publication électronique devra être fixée deux ans après la date
de publication papier. L’article sera ainsi accessible en texte intégral
deux ans après sa parution dans la revue papier.

Autres métadonnées
------------------

*Xpath*:

-  Langue :
   ``/tei:TEI/tei:teiHeader/tei:profileDesc/tei:langUsage/tei:language``
   avec une valeur au format ISO 639-1
-  Pagination :
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:sourceDesc/tei:biblFull/tei:publicationStmt/tei:idno[@type='pp']``

   -  La pagination papier d’un document peut être renseignée de
      différentes façons : en chiffres romains et petites capitales
      (V-XXV), en chiffres arabes (5-25).
   -  Toutes les valeurs sont valides. On indique la pagination sans les
      mentions p. ou pp., celles-ci étant généralement pris en charge
      par la maquette.

-  Numéro du document :
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:publicationStmt/tei:idno[@type='documentnumber']``
   Il s’agit d’une information éditoriale qui peut être affichée dans la
   maquette dans la référence électronique du document. Le numéro de
   document peut être utilisé, par exemple, pour faciliter la citation
   des documents électroniques.
-  Licence :
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:publicationStmt/tei:availability``
-  Notice bibliographique du document :
   ``/tei:TEI/tei:teiHeader/tei:fileDesc/tei:sourceDesc/tei:biblFull/tei:notesStmt/tei:note[@type='bibl']``
   Il est possible d'indiquer ici la référence bibliographique de
   l'édition papier de ce document.

*Exemple*:

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

