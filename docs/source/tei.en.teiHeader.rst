.. _tei-en-teiHeader:

teiHeader
##############################################

.. contents:: Summary
   :depth: 2

.. _tei-en-teiHeader-titres:   

Title, subtitle, suptitle, translated titles
=================================================

**Xpath**


| Title: ``/TEI/teiHeader/fileDesc/titleStmt/title[@type='main']``
| Subtitle: ``/TEI/teiHeader/fileDesc/titleStmt/title[@type='sub']``
| Suptitle: ``/TEI/teiHeader/fileDesc/titleStmt/title[@type='sup']``
| Translated title: ``/TEI/teiHeader/fileDesc/titleStmt/title[@type='alt' and @xml:lang]``


**Use recommandations**

-  single paragraph, without line break (``<lb>`` tag);
-  in lower case, except the first letter, not finish with a fullstop;
-  ``xml:lang`` attribute is required (ISO 639-1)

**Example**

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

.. _tei-en-teiHeader-auteurs: 

Authors, translators, academic editor, etc.
=================================================


**Xpath**

| Author: ``/TEI/teiHeader/fileDesc/titleStmt/author/name``
| Translator: ``/TEI/teiHeader/fileDesc/titleStmt/editor[@role='translator']/name``
| Editor: ``/TEI/teiHeader/fileDesc/titleStmt/editor[not(@role)]/name``
| Excavation director: ``/TEI/teiHeader/fileDesc/titleStmt/editor[@role='excavationsdirector']/name``
| Collaborator (for archeology): ``/TEI/teiHeader/fileDesc/titleStmt/editor[@role='collaborator']/name``


* Author's name

| Forename: ``/TEI/teiHeader/fileDesc/titleStmt/author/persName/forename``
| Surname: ``/TEI/teiHeader/fileDesc/titleStmt/author/persName/surname``

* Translator, Editor, Collaborator's name
   
| Forename: ``/TEI/teiHeader/fileDesc/titleStmt/editor/persName/forename``
| Surname: ``/TEI/teiHeader/fileDesc/titleStmt/editor/persName/surname``


* Author's description

| Description: ``/TEI/teiHeader/fileDesc/titleStmt/author/affiliation``
| Affiliation: ``/TEI/teiHeader/fileDesc/titleStmt/author/orgName``
| Position: ``/TEI/teiHeader/fileDesc/titleStmt/author/roleName[@type='function']``
| Title: ``/TEI/teiHeader/fileDesc/titleStmt/author/roleName[@type='honorific']``
| Email: ``/TEI/teiHeader/fileDesc/titleStmt/author/email``
| Web site: ``/TEI/teiHeader/fileDesc/titleStmt/author/ref[@type='website']``

* Translator, Editor, Collaborator's description

| Description: ``/TEI/teiHeader/fileDesc/titleStmt/editor/affiliation``
| Affiliation: ``/TEI/teiHeader/fileDesc/titleStmt/editor/orgName``
| Position: ``/TEI/teiHeader/fileDesc/titleStmt/editor/roleName[@type='function']``
| Title: ``/TEI/teiHeader/fileDesc/titleStmt/editor/roleName[@type='honorific']``
| Email: ``/TEI/teiHeader/fileDesc/titleStmt/editor/email``
| Web site: ``/TEI/teiHeader/fileDesc/titleStmt/editor/ref[@type='website']``


**Use recommandations**

- possibility to associate several authors, translators and editors to the document;
- possibility to provide a description for each contributor; general description is indicated in the tag ``<affiliation>``
- pay attention to case and spelling to avoid duplicates in indexes.

**Example**

.. code-block:: xml

  [...]
  <titleStmt>
  [...]
    <author>
      <name>Marin Dacos</name>
        <affiliation>
        Directeur du Cléo (Centre pour l'édition électronique ouverte)
        </affiliation>
        <roleName type="function">Directeur</roleName>
        <orgName>Cléo</orgName>
        <email>contact@openedition.org</email>
        <ref target="http://www.openedition.org" type="website">http://www.openedition.org</ref>
        <roleName type="honorific">M.</roleName>
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

.. _tei-en-teiHeader-index:

Index: keywords; geography; chronology; themes; person cited
=================================================================

**Xpath**

| Index : ``/TEI/teiHeader/profileDesc/textClass/keywords[@scheme and @xml:lang]/list/item``
   

| Persons index, using the tag ``<persName>``:
| ``/TEI/teiHeader/profileDesc/textClass/keywords[@scheme='personcited']/list/item/persName/forename``
| ``/TEI/teiHeader/profileDesc/textClass/keywords[@scheme='personcited']/list/item/persName/surname``

**Use recommandations**

- allowed values for the attribute 'scheme'

 * ``<keywords scheme="keywords" lang="en">`` : keywords index (the attribute 'xml:lang' is required in ISO 639-1 format);
 * ``<keywords scheme="geographical">`` : geographical index, places;
 * ``<keywords scheme="chronological">`` : chronological index, times, periods;
 * ``<keywords scheme="subject">`` : topical index, subjects;
 * ``<keywords scheme="personcited">`` : person Cited (persons index).

- pay attention to case and spelling to avoid duplicates in indexes.


**Example**

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

.. _tei-en-teiHeader-dates:

Print and electronic publication dates
========================================

**Xpath**

| Electronic publication date: ``/TEI/teiHeader/fileDesc/publicationStmt/date``
| Print publication date: ``/TEI/teiHeader/fileDesc/sourceDesc/biblFull/publicationStmt/date``

**Use recommandations**

- date in the DD/MM/YYYY format;
- do not use for Openedition Books;
- for OpenEdition Journals you should indicate an electronic publication date, otherwise it will be automatically set by Lodel and updated when the document is reloaded.

*Electronic publication dates for journals with embargo periods*

- corresponds to the date of availability ot the document, calculated by adding the embargo duration to the print publication date;
- used by Lodel to manage the availability of the document : display metadata and summary during the embargo period then provide full text.

**Example**

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






.. _tei-en-teiHeader-autres-md:

Other metadata
======================================


**Xpath**

| Language: ``/TEI/teiHeader/profileDesc/langUsage/language``
| Pagination: ``/TEI/teiHeader/fileDesc/sourceDesc/biblFull/publicationStmt/idno[@type='pp']``
| Document number: ``/TEI/teiHeader/fileDesc/publicationStmt/idno[@type='documentnumber']``
| Licence: ``/TEI/teiHeader/fileDesc/publicationStmt/availability``
| Bibliographical notice for the document: ``/TEI/teiHeader/fileDesc/sourceDesc/biblFull/notesStmt/note[@type='bibl']``

**Use recommandations**

- Language: with a value in ISO 639-1 format;
- Pagination: indicated in Roman numbers or and small capitals (V-XXV), or Arabic numbes (5-25), without using entering p. or pp.;
- Document number: editorial information displayed in the document’s electronic reference, used, to facilitate the citation of electronic;
- Licence : add an entry in licence index;
- Biliographical notice : used to indicate the bibliographical reference of the document’s print edition.


**Example**

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

