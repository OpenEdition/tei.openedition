Documentation TEI openedition : https://github.com/OpenEdition/tei.openedition/wiki 


Validation with online tei.openedition.1.5.1 schema


<?xml version="1.0" encoding="UTF-8"?>
<TEI 
	xmlns="http://www.tei-c.org/ns/1.0" 
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://www.tei-c.org/ns/1.0 http://lodel.org/ns/tei.openedition.1.5.1/tei.openedition.1.5.1.xsd">




Modification de la version du schema TEI (modification de l'ODD)

En cas de modification de la version du schema TEI, il est impératif de modifier dans l'ODD (tei.openedition.XXX.odd.xml) la valeur de l'attribut "ident" de l'élément "schemaSpec" en utilisant le nom du fichier xsd attendu sans l'extension .xsd. C'est nécessaire car c'est sur cette base que seront créées les références à tei.openedition.XXX.xsd dans les fichiers xml.xsd et dcr.xsd.
Exemple dans tei.openedition.1.3.2.odd.xml :
	<schemaSpec ident="tei.openedition.1.3.2" start="TEI" source="http://www.tei-c.org/Vault/P5/2.6.0/xml/tei/odd/p5subset.xml">
