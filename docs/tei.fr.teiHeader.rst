.. _tei-fr-teiHeader:


teiHeader
############################################

.. contents:: Sommaire
   :depth: 2


.. _tei-fr-teiHeader-titres:


titres, sous-titres, surtitres, titres traduits
=================================================

**XPath**

| Titre : ``/TEI/teiHeader/fileDesc/titleStmt/title[@type='main']``
| Sous-titre : ``/TEI/teiHeader/fileDesc/titleStmt/title[@type='sub']``
| Surtitre : ``/TEI/teiHeader/fileDesc/titleStmt/title[@type='sup']``
| Titres traduits : ``/TEI/teiHeader/fileDesc/titleStmt/title[@type='alt' and @xml:lang]``


**Recommandations d'usage**

-  pas de saut de ligne (balise ``<lb />``), un seul paragraphe ;
-  en minuscules sauf initiale, non terminés par un point ;
-  pour les titres traduits l'attribut ``xml:lang`` est obligatoire avec un valeur au format ISO 639-1.


**Exemple**

.. code-block:: xml

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



.. _tei-fr-teiHeader-auteurs:

Auteurs, éditeurs, traducteurs
=============================================

**XPath**

| Auteur : ``/TEI/teiHeader/fileDesc/titleStmt/author/``
| Traducteur : ``/TEI/teiHeader/fileDesc/titleStmt/editor[@role='translator']``
| Éditeur scientifique : ``/TEI/teiHeader/fileDesc/titleStmt/editor[not(@role)]``
| Directeur de fouilles : ``/TEI/teiHeader/fileDesc/titleStmt/editor[@role='excavationsdirector']``
| Collaborateur : ``/TEI/teiHeader/fileDesc/titleStmt/editor[@role='collaborator']``

- Noms des auteurs

| Prénom : ``/TEI/teiHeader/fileDesc/titleStmt/author/persName/forename``
| Nom : ``/TEI/teiHeader/fileDesc/titleStmt/author/persName/surname``
  
- Noms des Traducteur, Éditeur scientifique, Directeur de fouilles, Collaborateur

| Prénom : ``/TEI/teiHeader/fileDesc/titleStmt/editor/persName/forename``
| Nom : ``/TEI/teiHeader/fileDesc/titleStmt/editor/persName/surname``

- Description des auteurs

| Description : ``/TEI/teiHeader/fileDesc/titleStmt/author/affiliation``
| Affiliation : ``/TEI/teiHeader/fileDesc/titleStmt/author/orgName``
| Fonction : ``/TEI/teiHeader/fileDesc/titleStmt/author/roleName[@type='function']``
| Préfixe : ``/TEI/teiHeader/fileDesc/titleStmt/author/roleName[@type='honorific']``
| Courriel : ``/TEI/teiHeader/fileDesc/titleStmt/author/email``
| Site web : ``/TEI/teiHeader/fileDesc/titleStmt/author/ref[@type='website']``

- Description des Traducteur, Éditeur scientifique, Directeur de fouilles, Collaborateur

| Description : ``/TEI/teiHeader/fileDesc/titleStmt/editor/affiliation``
| Affiliation : ``/TEI/teiHeader/fileDesc/titleStmt/editor/orgName``
| Fonction : ``/TEI/teiHeader/fileDesc/titleStmt/editor/roleName[@type='function']``
| Préfixe : ``/TEI/teiHeader/fileDesc/titleStmt/editor/roleName[@type='honorific']``
| Courriel : ``/TEI/teiHeader/fileDesc/titleStmt/editor/email``
| Site web : ``/TEI/teiHeader/fileDesc/titleStmt/editor/ref[@type='website']``

.. TODO : vérifier usage de l'élément s


**Recommandations d'usage**

- possibilité d'indiquer plusieurs auteurs, traducteurs, etc. pour le document ;
- possibilité d'ajouter des descriptions pour chacun des contributeurs, la description générale est indiquée dans la balise ``<affiliation>`` ;
- attention à la casse et à l'orthographe pour éviter les doublons dans les index.

.. 2 possibilités d'encodage pour les noms de personnes : ``<name>`` ou ``<persName>``

.. Veillez à ce que les prénoms et noms soient affichés dans cet ordre et
.. en minuscule sauf initiale. Cet ordre est important car Lodel va en
.. déduire le prénom (premier mot) et le nom (deuxième mot) au moment de
.. l’importation. En cas de nom composé, il faut utiliser des espaces
.. insécables
.. (`http://fr.wikipedia.org/​wiki/​Espace_ins%C3%A9cable <http://fr.wikipedia.org/​wiki/​Espace_ins%C3%A9cable>`__)
.. entre les différentes parties du nom composé. De cette manière Lodel
.. distinguera correctement prénoms et noms. Cette recommandation n'est pas
.. nécessaire pour les prénoms composés.


**Exemple**

.. code-block:: xml

    [...]
    <titleStmt>
    [...]
       <author>
           <name>Marin Dacos</name>
           <affiliation>
               Directeur du Cléo (Centre pour l'édition électronique ouverte)
           </affiliation>
           <roleName type="function">
               Directeur
           </roleName>
           <orgName>
               Cléo
           </orgName>
           <email>
               contact@openedition.org
           </email>
           <ref target="http://www.openedition.org" type="website">http://www.openedition.org</ref>
           <roleName type="honorific">
               M.
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
    [...]


.. _tei-fr-teiHeader-index:

Index : mots clés, géographie, chronologie, thèmes, etc.
==========================================================

**XPath**

| Index :  ``/TEI/teiHeader/profileDesc/textClass/keywords[@scheme and @xml:lang]/list/item``

| Index de personnes, utilisation de ``<persName>`` : ``/TEI/teiHeader/profileDesc/textClass/keywords[@scheme]/list/item/persName/forename`` et ``/TEI/teiHeader/profileDesc/textClass/keywords[@scheme]/list/item/persName/surname``
  

**Recommandations d'usage**

- valeurs autorisées pour l'attribut 'scheme' :

 * ``<keywords scheme="keywords" lang="fr">`` : index de mots clés (attribut 'xml:lang' obligatoire avec une valeur au format ISO 639-1) ;
 * ``<keywords scheme="geographical">`` : index géographique, lieux ;
 * ``<keywords scheme="chronological">`` : index chronologique, périodes ;
 * ``<keywords scheme="subject">`` : index thématique, sujets ;
 * ``<keywords scheme="personcited">`` : personnes citées (index de personne).

- attention à la casse et à l'orthographe pour éviter les doublons dans les index.






.. Pour les personnes citées, on peut utiliser la balise ``<name>`` ou ``<persname>`` (se référer à la sections auteurs pour les précisions).


**Exemple**

.. code-block:: xml

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
                     <persName>
                         <forename>Olivier</forename>
                         <surname>Dumond</surname>
                     </persName>
                 </item>
             </list>
           </keywords>
   [...]

.. _tei-fr-teiHeader-dates:

Dates de publication
========================================

**XPath**

| Date de publication électronique : ``/TEI/teiHeader/fileDesc/publicationStmt/date``
| Date de publication papier : ``/TEI/teiHeader/fileDesc/sourceDesc/biblFull/publicationStmt/date``


**Recommandations d'usage**

- dates au format : JJ/MM/AAAA ;
- ne pas utiliser ces dates pour OpenEdition Books ;
- pour OpenEdition Journals il est important d'indiquer une date de publication électronique : en cas d'absence elle sera automatiquement renseignée sur Lodel et sera mis à jour en cas de rechargement du document.


*Date de publication électronique pour les revues à barrière mobile sur OpenEdition Journals*

- doit correspondre à la date de sortie de barrière mobile, calculée en ajoutant la durée de l'embargo à la date de publication papier ; 
- utilisée par Lodel pour gérer la disponibilité du document : affichage des métadonnées et résumé pendant la période de barrière mobile puis accès au texte intégral ;



**Exemple**

.. code-block:: xml

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


.. _tei-fr-teiHeader-autres-md:

Autres métadonnées
======================================

**XPath**

| Langue : ``/TEI/teiHeader/profileDesc/langUsage/language``
| Pagination : ``/TEI/teiHeader/fileDesc/sourceDesc/biblFull/publicationStmt/idno[@type='pp']``
| Numéro du document : ``/TEI/teiHeader/fileDesc/publicationStmt/idno[@type='documentnumber']``
| Licence : ``/TEI/teiHeader/fileDesc/publicationStmt/availability``
| Notice bibliographique du document : ``/TEI/teiHeader/fileDesc/sourceDesc/biblFull/notesStmt/note[@type='bibl']``

.. TODO : vérifie l'usage de licence et notice biblio

**Recommandations d'usage**

- Langue : valeur au format ISO 639-1 ;
- Pagination :  renseignée en chiffres romains et petites capitales (V-XXV) ou en chiffres arabes (5-25), sans les mentions p. ou pp. ;
- Numéro : information éditoriale affichée dans la référence électronique du document, utilisé pour faciliter la citation des documents électroniques ;
- Licence : utilisé pour renseigner la licence qui s'applique au document, ajoute une entrée à l'index licence du site ;
- Notice biblio : utilisée pour préciser la notice bibliographique du document papier

**Exemple**

.. code-block:: xml

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
