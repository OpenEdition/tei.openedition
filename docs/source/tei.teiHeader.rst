.. _tei-teiHeader:

teiHeader
####################################################################

.. contents:: Sommaire
   :depth: 5

.. sectnum::
   :depth: 5
   :start: 1

.. _tei-teiHeader-fileDesc:

fileDesc
====================================================================

L'élément ``fileDesc`` contient les métadonnées descriptives du document TEI organisées dans les éléments suivants : 

- ``titleStmt`` : titres et contributeurs 
- ``publicationStmt`` : informations relatives à la publication électronique
- ``sourceDesc`` : informations relatives à la source du document. Elles prendront un sens différent selon l'usage du document TEI 

.. _tei-teiHeader-titleStmt:

titleStmt
--------------------------------------------------------------------

.. _tei-teiHeader-titres:

titres, sous-titres, surtitres, titres traduits
********************************************************************

**XPath**

| Titre : ``/TEI/teiHeader/fileDesc/titleStmt/title[@type='main']``
| Sous-titre : ``/TEI/teiHeader/fileDesc/titleStmt/title[@type='sub']``
| Surtitre : ``/TEI/teiHeader/fileDesc/titleStmt/title[@type='sup']``
| Titres traduits : ``/TEI/teiHeader/fileDesc/titleStmt/title[@type='alt' and @xml:lang]``


**Recommandations d'usage**

-  pas de saut de ligne (balise ``<lb />``), un seul élément ``title`` par type ;
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



.. _tei-teiHeader-auteurs:

Auteurs, éditeurs, traducteurs
********************************************************************

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


.. _tei-teiHeader-publicationStmt:

publicationStmt
--------------------------------------------------------------------

.. _tei-teiHeader-date:

Date de publication électronique
********************************************************************

**XPath**

| Date de publication électronique : ``/TEI/teiHeader/fileDesc/publicationStmt/date``


**Recommandations d'usage**

- dates au format JJ/MM/AAAA ;
- ne pas utiliser pour OpenEdition Books (la date est définie au niveau du livre) ;
- pour OpenEdition Journals il est important d'indiquer une date de publication électronique : en cas d'absence elle sera automatiquement renseignée par Lodel et sera mis à jour en cas de rechargement du document.

*Date de publication électronique pour les revues à barrière mobile sur OpenEdition Journals*

- doit correspondre à la date de sortie de barrière mobile, calculée en ajoutant la durée de l'embargo à la date de publication papier ; 
- utilisée par Lodel pour gérer la disponibilité du document : affichage des métadonnées et résumé pendant la période de barrière mobile puis accès au texte intégral ;


.. _tei-teiHeader-publisher:

Éditeur, Distributeur
********************************************************************

**XPath**

| éditeur : ``/TEI/teiHeader/fileDesc/publicationStmt/publisher``
| distributeur : ``/TEI/teiHeader/fileDesc/publicationStmt/distributor``


**Recommandations d'usage**

- Utilisés dans la TEI produite en sortie de la plateforme uniquement.

**Exemple**

.. code-block:: xml

    <publicationStmt>
        [...]
        <publisher>Université de Poitiers</publisher>
        <distributor>OpenEdition</distributor>
        [...]
    </publicationStmt>

.. _tei-teiHeader-idno:

Identifiant
********************************************************************

**XPath**

| Numéro du document : ``/TEI/teiHeader/fileDesc/publicationStmt/idno[@type='documentnumber']``
| URL : ``/TEI/teiHeader/fileDesc/publicationStmt/idno[@type='url']``
| DOI : ``/TEI/teiHeader/fileDesc/publicationStmt/idno[@type='doi']``


**Recommandations d'usage**

- Numéro du document : information éditoriale affichée dans la référence électronique du document, utilisé pour faciliter la citation des documents électroniques ;
- URL et DOI : utilisés dans la TEI produite en sortie de la plateforme uniquement.

**Exemple**

.. code-block:: xml

    <publicationStmt>
        [...]
        <idno type="documentnumber">24</idno>
        <idno type="url">http://journals.openedition.org/remi/7777</idno>
        <idno type="doi">10.4000/remi.7777</idno>
        [...]
    </publicationStmt>



.. _tei-teiHeader-availability:

Licence
********************************************************************

**XPath**

| Licence : ``/TEI/teiHeader/fileDesc/publicationStmt/availability``

**Recommandations d'usage**

- Utilisé pour renseigner la licence qui s'applique au document, ajoute une entrée à l'index licence du site.

**Exemple**

.. code-block:: xml

    <publicationStmt>
        [...]
        <availability>La revue In Situ. Au regard des sciences sociales 
                      est mise à disposition selon les termes de la Licence Creative Commons 
                      Attribution - Pas d'Utilisation Commerciale - Pas de Modification 4.0 International.
        </availability>
        [...]
    </publicationStmt>




.. _tei-teiHeader-sourceDesc:

sourceDesc
--------------------------------------------------------------------	

.. note::

   L'élément ``sourceDesc`` contient les informations relatives au document source qui a servi à produire ce document TEI. 
   Il prendra un sens différent selon l'usage du document TEI :

   - à l'import dans Lodel, ``sourceDesc`` contiendra les métadonnées relatives à l'édition papier le cas échéant ;
   - à l'export ``sourceDesc`` contiendra les métadonnées du contexte de publication sur OpenEdition (sur la revue, le numéro, le livre...).


.. _tei-teiHeader-biblFull:

biblFull
********************************************************************

.. warning::

   L'élément ``biblFull`` n'est plus supporté à partir de la version 1.6.2 du schéma XML TEI OpenEdition

**XPath**

| Date de publication papier : ``/TEI/teiHeader/fileDesc/sourceDesc/biblFull/publicationStmt/date``
| Pagination : ``/TEI/teiHeader/fileDesc/sourceDesc/biblFull/publicationStmt/idno[@type='pp']``
| Notice bibliographique du document : ``/TEI/teiHeader/fileDesc/sourceDesc/biblFull/notesStmt/note[@type='bibl']``

**Recommandations d'usage**

- Date de publication papier : dates au format JJ/MM/AAAA ; ne pas utiliser cette date pour OpenEdition Books ;
- Pagination :  renseignée en chiffres romains (V-XXV) ou en chiffres arabes (5-25), sans les mentions p. ou pp. ;
- Notice biblio : utilisée pour préciser la notice bibliographique du document papier.


**Exemple**

.. code-block:: xml

    [...]
    </publicationStmt>
    <sourceDesc>
        <biblFull>
            <publicationStmt>
                <date>01/07/2008</date> <!--date de publication papier-->
                <idno type="pp">10-27</idno>
            </publicationStmt>
           <notesStmt>
               <note type="bibl">Référence bibliographique de l'édition papier de cet article.</note>
           </notesStmt>
    [...]
        </biblFull>
    </sourceDesc>


.. _tei-teiHeader-biblStruct:

biblStruct
********************************************************************

.. warning::

   L'élément ``biblStruct`` est supporté :
   
   - import OEJ et OEB : à partir de la version 1.6.2 du schéma XML TEI OpenEdition ;
   - export OE : à partir de la version 1.6.0 du schéma XML TEI OpenEdition.


.. _tei-teiHeader-biblStruct-analytic:

biblStruct/analytic
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**XPath**

| Titre : ``/TEI/teiHeader/sourceDesc/biblStruct/analytic/title[@type='main']``
| Sous-titre : ``/TEI/teiHeader/sourceDesc/biblStruct/analytic/title[@type='sub']``
| Surtitre : ``/TEI/teiHeader/sourceDesc/biblStruct/analytic/title[@type='sup']``
| Titres traduits : ``/TEI/teiHeader/sourceDesc/biblStruct/analytic/title[@type='alt' and @xml:lang]``
| Auteur : ``/TEI/teiHeader/sourceDesc/biblStruct/analytic/author/``
| Traducteur : ``/TEI/teiHeader/sourceDesc/biblStruct/analytic/editor[@role='translator']``
| Éditeur scientifique : ``/TEI/teiHeader/sourceDesc/biblStruct/analytic/editor[not(@role)]``
| Directeur de fouilles : ``/TEI/teiHeader/sourceDesc/biblStruct/analytic/editor[@role='excavationsdirector']``
| Collaborateur : ``/TEI/teiHeader/sourceDesc/biblStruct/analytic/editor[@role='collaborator']``



**Recommandations d'usage**

- Utilisé uniquement à l'export TEI OE, l'élément ``analytic`` contient les titres et les contributeurs du document TEI.

.. _tei-teiHeader-biblStruct-monogr:

biblStruct/monogr
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**XPath**

- Titres

| Titre de la revue (revue) :
| ``/TEI/teiHeader/sourceDesc/biblStruct/monogr/title[@level='j']``
| Titre de la rubrique pour les articles publiés hors numéro (revue) : 
| ``/TEI/teiHeader/sourceDesc/biblStruct/monogr/title[@level='s']``
| Titre traduit de la rubrique pour les articles publiés hors numéro (revue) : 
| ``TEI/teiHeader/sourceDesc/biblStruct/monogr/title[@level='s' and @type='alt']``
| Titre du livre ou du numéro (livre et revue) : 
| ``/TEI/teiHeader/sourceDesc/biblStruct/monogr/title[@level='m']``
| Titre traduit du livre ou du numéro (livre et revue) : 
| ``/TEI/teiHeader/sourceDesc/biblStruct/monogr/title[@level='m' and @type='alt']``

- Identifiants (revue)

| ISSN électronique :
| ``/TEI/teiHeader/sourceDesc/biblStruct/monogr/idno[@type='eISSN']``
| ISSN édition papier :
| ``/TEI/teiHeader/sourceDesc/biblStruct/monogr/idno[@type='pISSN']``
| URL du numéro : 
| ``/TEI/teiHeader/sourceDesc/biblStruct/monogr/idno[@type='url' and @subtype='issue']``
| DOI du numéro : 
| ``/TEI/teiHeader/sourceDesc/biblStruct/monogr/idno[@type='doi' and @subtype='issue']``
| URL de la rubrique : 
| ``/TEI/teiHeader/sourceDesc/biblStruct/monogr/idno[@type='url' and @subtype='serie']``
| DOI de la rubrique : 
| ``/TEI/teiHeader/sourceDesc/biblStruct/monogr/idno[@type='doi' and @subtype='serie']``

- Identifiants (livre)

| ISBN électronique :
| ``/TEI/teiHeader/sourceDesc/biblStruct/monogr/idno[@type='eISBN']``
| ISBN édition papier : 
| ``/TEI/teiHeader/sourceDesc/biblStruct/monogr/idno[@type='pISBN']``
| URL du livre : 
| ``/TEI/teiHeader/sourceDesc/biblStruct/monogr/idno[@type='url' and @subtype='book']``
| DOI du livre : 
| ``/TEI/teiHeader/sourceDesc/biblStruct/monogr/idno[@type='doi' and @subtype='book']``

- Informations sur l'édition papier

| Pagination de l'édition papier (livre et revue):
| ``/TEI/teiHeader/sourceDesc/biblStruct/monogr/imprint/biblScope[@unit='page']``
| Numéro (revue) :
| ``/TEI/teiHeader/sourceDesc/biblStruct/monogr/imprint/biblScope[@unit='issue']``
| Date de publication papier (livre et revue): 
| ``/TEI/teiHeader/sourceDesc/biblStruct/monogr/imprint/date[@type='published']``  
| Éditeur (livre et revue): 
| ``/TEI/teiHeader/sourceDesc/biblStruct/monogr/imprint/publisher``


**Recommandations d'usage**

- dans l'export TEI OE, l'élément ``monogr`` contient les métadonnées relatives à l'environnement de publication du document TEI (livre, numéro, rubrique, revue) ;
- pour l'import d'articles sur OpenEdition Journals (import OJ) ou de chapitres des livres sur OpenEdition Books (import OB), les éléments suivants sont utilisables :

   - pagination de l'édition papier (import OJ et import OB) ; 
   - date de publication papier (import OJ). Sur OpenEdition Books la date de publication papier est définie au niveau du livre.

- Date de publication papier : dates au format JJ/MM/AAAA ; ne pas utiliser cette date pour OpenEdition Books ;
- Pagination :  renseignée en chiffres romains (V-XXV) ou en chiffres arabes (5-25), sans les mentions p. ou pp. ;
- Notice biblio : utilisée pour préciser la notice bibliographique du document papier.

.. _tei-teiHeader-biblStruct-series:

biblStruct/series
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**XPath**

| Titre de la collection : 
| ``/TEI/teiHeader/sourceDesc/biblStruct/series/title[@level='s']``
| Titre traduit de la collection : 
| ``/TEI/teiHeader/sourceDesc/biblStruct/series/title[@level='s' and @type='alt']``
| ISSN électronique de la collection : 
| ``/TEI/teiHeader/sourceDesc/biblStruct/series/idno[@type='eISSN']``
| ISSN papier de la collection :
| ``/TEI/teiHeader/sourceDesc/biblStruct/series/idno[@type='pISSN']``
| URL de la collection : 
| ``/TEI/teiHeader/sourceDesc/biblStruct/series/idno[@type='url']``

**Recommandations d'usage**

- Dans l'export OE pour les **chapitres de livre uniquement**, l'élément ``series`` contient les métadonnées relatives à l'environnement de publication du document TEI (collection).


Exemples biblStruct
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


**Exemple d'article de revue (export OE)**

.. code-block:: xml

    [...]
    <sourceDesc>
       <biblStruct type="article">
            <analytic>
                <title level="a" type="main">La formation des étudiants marocains dans les pays de l’Est de l’Europe (1960-2015)</title>
                <title level="a" type="alt" xml:lang="en">Moroccan Students’ Training in Eastern Europe Countries (1960-2015)</title>
                <title level="a" type="alt" xml:lang="es">La formación de los estudiantes marroquíes en los países de Europa del Este (1960-2015)</title>
                <author>
                    <persName>
                        <forename>Kamal</forename>
                        <surname>Mellakh</surname>
                    </persName>
                    <affiliation>
                        Enseignant-chercheur, Département de sociologie, Faculté des lettres et sciences humaines de Mohammedia, Université Hassan II, Casablanca B.P 546, Mohammedia, Maroc ; kmellakh@yahoo.fr
                    </affiliation>
                </author>
            </analytic>
            <monogr>
                <title level="j">Revue européenne des migrations internationales</title>
                <idno type="eISSN">1777-5418</idno>
                <idno type="pISSN">0765-0752</idno>
                <title level="m">Former des élites : mobilités des étudiants d'Afrique au nord du Sahara dans les pays de l'ex-bloc socialiste</title>
                <title level="m" type="alt" xml:lang="en">Training Elites: Mobilities of Students of Africa North of Sahara to the Former Socialist Block</title>
                <title level="m" type="alt" xml:lang="es">Formar a las élites: movilidades de los estudiantes de África del norte del Sáhara hacia el ex-bloque socialista</title>
                <idno type="doi" subtype="issue">10.4000/remi.7751</idno>
                <idno type="url" subtype="issue">http://journals.openedition.org/remi/7751</idno>
                <imprint>
                    <publisher>Université de Poitiers</publisher>
                    <biblScope unit="page">39-56</biblScope>
                    <biblScope unit="issue">vol. 32 - n°2</biblScope>
                    <date type="published" when="2016-10-24">2016-10-24</date>
                </imprint>
            </monogr>
        </biblStruct>
    </sourceDesc> 


**Exemple de chapitre de livre (export OE)**

.. code-block:: xml

    [...]
    <biblStruct type="chapter">
        <analytic>
            <title level="a" type="main">Albert Cossery écrit‑il arabe ?</title>
            <author>
                <persName>
                    <forename>Frédéric</forename>
                    <surname>Lagrange</surname>
                </persName>
            </author>
        </analytic>
        <monogr>
            <title level="m">Savants, amants, poètes et fous</title>
            <idno type="pISBN">9782351597521</idno>
            <idno type="eISBN">9782351595503</idno>
            <idno type="doi" subtype="book">10.4000/books.ifpo.13332</idno>
            <idno type="url" subtype="book">http://books.openedition.org/ifpo/13332</idno>
            <imprint>
                <publisher>Presses de l’Ifpo</publisher>
                <publisher>Centre français d'archéologie et de sciences sociales (Cefas)</publisher>
                <biblScope unit="page">133-157</biblScope>
                <date type="published" when="2019">2019</date>
            </imprint>
        </monogr>
        <series>
            <title level="s">Contemporain publications</title>
            <idno type="pISSN">2225-7578</idno>
            <idno type="url">http://books.openedition.org/ifpo/62</idno>
        </series>
    </biblStruct>


 
.. _tei-teiHeader-encodingDesc:

encodingDesc
==========================================================

Contient des déclarations de mise en formes dans l'élément ``tagsDecl``. Voir :ref:`tei-teibody-mises-en-forme` 


.. _tei-teiHeader-profileDesc:

profileDesc
==========================================================

 
.. _tei-teiHeader-index:

Index : mots clés, géographie, chronologie, thèmes, etc.
----------------------------------------------------------

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


.. _tei-teiHeader-langue:

Langue
----------------------------------------------------------

**XPath**

| Langue : ``/TEI/teiHeader/profileDesc/langUsage/language``

**Recommandations d'usage**

- Langue : valeur au format ISO 639-1 ;

**Exemple**

.. code-block:: xml

   <profileDesc>
       <langUsage>
           <language>fr</language>
       </langUsage>
   [...]
