# XML/TEI OpenEdition Schema

This Git project contains TEI schema versions used by the OpenEdition Books and OpenEdition Journals platforms. It is associated to the revuesorg editorial model shipped with the Lodel software https://github.com/OpenEdition/lodel

Among the different XML encoding standards for machine-readable texts, the TEI ([Text Encoding Initiative](http://www.tei-c.org/)) is probably the most comprehensive and mature. The TEI Guidelines define some 500 different textual components and concepts (word, sentence, character, glyph, person, etc.). Any particular usage of the TEI supposes a customization of the TEI to their specificities, so as to adapt and constraint the richness of the TEI to a well scoped and tuned schema. The TEI community has created a specification language called ODD [("One Document Does it all")](http://www.tei-c.org/Guidelines/Customization/odds.xml) to modify the general TEI schema. Having ODD descriptions, it is possible with a tool called Roma to generate automatically customised TEI schemas (xsd, relaxNG, etc.) and some documentation.

In this project :
- the odd directory containes the ODD description
- the xsd directory contains the ROMA-generated XSD schema

When validating an XML file against this schema, you can use the Schema locally on your machine, or the schema published here:  http://lodel.org/ns (see the /doc directory for an example schema declaration in the XML file).

See: https://github.com/OpenEdition/tei.openedition/releases for the successive versions of the Schema.

The usage recommendations and examples are here: https://github.com/OpenEdition/tei.openedition/wiki  

# Schema TEI OpenEdition 

Ce projet versionne le schéma TEI utilisé sur les plateformes d'OpenEdition Journals et d'OpenEdition Books. Il correspond au modèle éditorial revuesorg distribué avec Lodel https://github.com/OpenEdition/lodel

Parmi les standards d'encodage XML d'un texte, TEI ([Text Encoding Initiative](http://www.tei-c.org/)) est sans doute le plus complet et le plus mûr. The TEI Guidelines define some 500 different textual components and concepts (word, sentence, character, glyph, person, etc.). Any particular usage of the TEI supposes a customization of the TEI to their specificities, so as to adapt and constraint the richness of the TEI to a well scoped and tuned schema. The TEI community has created a specification language called ODD [("One Document Does it all")](http://www.tei-c.org/Guidelines/Customization/odds.xml) to modify the general TEI schema. Having ODD descriptions, it is possible with a tool called Roma to generate automatically customised TEI schemas (xsd, relaxNG, etc.) and some documentation.

In this project :
- the odd directory containes the ODD description
- the xsd directory contains the ROMA-generated XSD schema

Pour valider un fichier XML avec ce schéma, il est possible d'utiliser le schéma en local ou d'utiliser le schéma xsd publié à l'adresse http://lodel.org/ns (se reporter au répertoire /doc pour un exemple de déclaration du schéma dans le fichier xml).

Se reporter aux releases (https://github.com/OpenEdition/tei.openedition/releases) pour connaitre les évolutions du schéma.

Les recommandations d'usage sont décrites avec des exemples dans le wiki du projet (https://github.com/OpenEdition/tei.openedition/wiki) 
