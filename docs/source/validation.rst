Validation with XML Schema
#########################################################

All versions of OpenEdition TEI XML Schema are available 

- on the GitHub repository: https://github.com/OpenEdition/tei.openedition/tree/master/xsd
- on lodel.org: http://lodel.org/ns/tei

You can validate your TEI file in your XML editor using the following attributes in the root element (``/TEI``) of the TEI file.

.. code:: xml

   <?xml version="1.0" encoding="UTF-8"?>
   <TEI 
	xmlns="http://www.tei-c.org/ns/1.0" 
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://www.tei-c.org/ns/1.0 http://lodel.org/ns/tei/tei.openedition.1.5.2/tei.openedition.1.5.2.xsd">

You can also validation your XML files on Linux with xmllint:

.. code:: shell 

  xmllint --schema http://lodel.org/ns/tei/tei.openedition.1.5.2/tei.openedition.1.5.2.xsd XML-FILE.tei.xml --noout 




