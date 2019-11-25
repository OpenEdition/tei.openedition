.. _tei-fr-back:


text/back
############################################

.. contents:: Sommaire
   :depth: 4

.. sectnum::
   :depth: 4
   :start: 4

.. _tei-fr-teiback-biblio:


Bibliographie
============================================

**Xpath**

| Section bibliographie : ``/TEI/text/back/div[@type='bibliography']/listBibl``
| Référence bibliographique : ``/TEI/text/back/div[@type='bibliography']/listBibl/bibl``
| Intertitres : ``/TEI/text/back/div[@type='bibliography']/listBibl/head[@subtype='leveln']`` 

**Recommandations d'usage**

- la section bibliographie est définie avec une balise ``<div type='bibliography'>`` et commence par une balise par une balise ``<listBibl>`` ;
- ``<listBibl>`` ne peut contenir de balises ``<div>`` ; 
- utilisation des balises ``<head>`` pour placer des intertitres, l'attribut 'leveln' peut prendre toutes les valeurs comprises entre 'level1' et 'level6' ;
- les balises ``<listBibl>`` peuvent être imbiquées en fonction de la structuration des niveaux de titres dans la bibliographie ;
- les références bibliographiques sont indiquées avec des balises ``<bibl>``

**Exemple**

.. code-block:: xml

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
    </listBibl>
    </div>
  [...] 
  </back>
  [...]



.. _tei-fr-teiback-annexes:   

Annexes
============================================

**Xpath**

Annexes :  ``/TEI/text/back/div[@type='appendix']``

**Recommandations d'usage**

- La section annexe est définie avec une balise ``<div type='appendix'>``
- tous les éléments utilisables dans ``<body>`` sont utilisables dans cette section


**Exemple**

.. code-block:: xml

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
