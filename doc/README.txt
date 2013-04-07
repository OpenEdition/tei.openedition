08/04/2013

Les modifications suivantes sont à faire sur le schéma W3C fourni par Roma pour le rendre valide et fonctionnel.



Dans le fichier principal (tei.openedition.1.0.xsd) :

1. Supprimer tous les " form=unqualified" en les remplaçant par "" (chaîne vide). Il y a 24 occurences.



2. Dans la définition de l'élément 'list', dans la définition de son attribut 'type', supprimer la chaîne 'default="simple"'

<xs:element name="list">
  <xs:annotation>
    <xs:documentation> (liste) contient une suite d'items ordonnés dans une liste. [3.7. ]</xs:documentation>
  </xs:annotation>
  <xs:complexType>
    <xs:group maxOccurs="unbounded" ref="ns1:item"/>
    <xs:attributeGroup ref="ns1:att.global.attribute.xmlid"/>
    <xs:attributeGroup ref="ns1:att.global.attribute.rend"/>
    <xs:attributeGroup ref="ns1:att.global.attribute.rendition"/>
    <xs:attribute name="type" default="simple">                        <!-- // ICI \\ -->
      <xs:annotation>
        <xs:documentation>décrit la forme de la liste.</xs:documentation>
      </xs:annotation>
      <xs:simpleType>
        <xs:restriction base="xs:token">
          <xs:enumeration value="ordered"/>
          <xs:enumeration value="unordered"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:attribute>
  </xs:complexType>
</xs:element>



3. En tête de fichier, supprimer la ligne suivante :
<xs:import namespace="http://www.isocat.org/ns/dcr" schemaLocation="dcr.xsd"/>

Une erreur de validation apparait, liée à la disparition de l'espace de nom "dcr".



4. Supprimer la séquence suivante qui utilise l'espace de nom dcr :

<xs:attributeGroup name="att.datcat.attribute.datcat">
    <xs:attribute ref="dcr:datcat"/>
</xs:attributeGroup>
<xs:attributeGroup name="att.datcat.attribute.valueDatcat">
    <xs:attribute ref="dcr:valueDatcat"/>
</xs:attributeGroup>



5. Supprimer la déclaration de l'espace de nom dcr dans la balise racine :
xmlns:dcr="http://www.isocat.org/ns/dcr"



6. En tête de fichier, remplacer la ligne suivante : 
<xs:import namespace="http://www.w3.org/XML/1998/namespace" schemaLocation="xml.xsd"/>
Par celle-ci :
<xs:import namespace="http://www.w3.org/XML/1998/namespace" schemaLocation="http://www.w3.org/2001/xml.xsd"/>



7. Supprimer les fichiers dcr.xsd et xml.xsd