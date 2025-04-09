Validation avec le schéma XML
#########################################################

Toutes les versions du schéma XML TEI sont disponibles

- sur Github : https://github.com/OpenEdition/tei.openedition/tree/master/xsd
- sur lodel.org: http://lodel.org/ns/tei

Vous pouvez valider vos fichiers TEI avec votre éditeur XML en utilisant les attributs suivants sur l'élément racine ``/TEI`` du fichier TEI :

.. code-block:: xml

   <?xml version="1.0" encoding="UTF-8"?>
   <TEI 
	xmlns="http://www.tei-c.org/ns/1.0" 
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://www.tei-c.org/ns/1.0 https://lodel.org/ns/tei/tei.openedition.1.6.4/document.xsd">


Vous pouvez également valider vos fichiers XML sur Linux avec xmllint :

.. code-block:: shell 

  xmllint --schema https://lodel.org/ns/tei/tei.openedition.1.6.4/document.xsd XML-FILE.tei.xml --noout 








