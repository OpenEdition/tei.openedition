.. _changelog:

Changelog and roadmap
###############################




Version 1.6.2 (not yet released)
=========================================

- remove sourceDesc/biblFull



Version 1.6.1
=========================================


- new attribute support
    + head\@rend
    + head\@rendition
- tag nesting
    + allow <q>, <table> in <note>
    + allow <ref> in
    + allow <list>, <p>, <q> in <cell>
    + allow <list> in <div>
- xsd
    + add xsd/tei.openedition.1.6.1
- other
    + update <body> behaviour and avoid the xsd/tei.openedition.1.6.0/document.xsd validity error: 'cos-nonambig' (using ROMA 5.0.0 with TEI 3.5.0). See commit `6ade00f <https://github.com/OpenEdition/tei.openedition/commit/6ade00f94960c97f684077615217a6fbff87809e>`_



Version 1.6.0
=========================================

- odd
    + schemaSpec/source use now https
    + remove release number from odd now useless with roma 5.0.0
    + rename odd/tei.openedition.odd -> odd/tei.openedition.odd.xml
    + rm 1st char <U+FEFF> in odd
    + add schemaLocation to tei.openedition.odd.xml
- new elements support:
    + distributor: allow distributor in teiHeader
    + biblStruct (usefull in teiHeader/fileDesc/sourceDesc for TEI export after publication)
        * analytic
        * monogr
        * imprint
        * series
    + schemaRef: ref to odd source in xsd schema
- new attribute support:
    + biblScope\@unit
    + date\@type: used in publicationStmt (published date)
- tag nesting
    + allow <figure> in <hi>
    + allow <figure> in <cell>
    + allow <q> in <item>
    + allow <listBibl> in <body>
- xsd
    + add xsd/tei.openedition.1.6.0



Updates before Version 1.5.2
===============================

- 11/10/2017 : correction on math formula examples
- 06/01/2017: 2 contributors : collaborator and excavationsdirector, person cited, math formula
- 03/01/2017: specifications for ``//tei:p[@rend='break']``
- 14/12/2016: fix ``<hi rend="small-caps">``
- 12/12/2016: list style type
- 10/23/2015: specifications for ``<persName>`` added.
- 04/28/2015: specifications for linguistic examples added.
- 04/27/2015: correction for epigraphs: unlike what was written in this documentation before this day, epigraphs must be included in the ``<body>`` element, not in the ``<front>`` element.

