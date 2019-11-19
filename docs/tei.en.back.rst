.. _tei-en-back:

back
############################################

.. contents:: Summary
   :depth: 2


.. _tei-en-teiback-biblio:


Bibliography
============================================

**Xpath**

| Bibliography section: ``/TEI/text/back/div[@type='bibliography']/listBibl``
| Bibliographical reference:``/TEI/text/back/div[@type='bibliography']//listBibl/bibl``
| Section titles: ``/TEI/text/back/div[@type='bibliography']//listBibl/head[@subtype='leveln']``

**Use recommandations**

- bibliographies are created using the ``<listBibl>`` and ``<bibl>`` tags;
- ``<listBibl>`` cannot contain sections ``<div>``;
- ``<head>`` tags can be used to insert section titles, 'leveln' attributes can take all values between 'level1' and 'level6';
- the ``<listBibl>`` tags can be nested according to the structuring of title levels in the bibliography;
- bibliographical reference are indicated with the ``<bibl>`` tag.


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


.. _tei-en-teiback-annexes:   

Annexes
============================================

**Xpath**

Annexes : ``/TEI/text/back/div[@type='appendix']``



**Use recommandations**

- annexes section is defined with the element ``<div type="appendix">``;
- all elements applicable in the ``<body>`` can be used in this section.

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

