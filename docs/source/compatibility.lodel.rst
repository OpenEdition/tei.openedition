
.. _compatibility-lodel:


Environnement Lodel et schéma TEI
##########################################

Les sites sous `Lodel <https://github.com/OpenEdition/lodel>`_ doivent utiliser un des modèles éditoriaux compatibles avec la version du schéma TEI pour importer des documents. Le modèle éditorial contient les XPath qui permettent au parser TEI de Lodel d'alimenter la base de données, il est donc impératif de suivre la compatibilité des versions entre le modèle éditorial et le schéma.

Pour l'import de document au format texte (doc, docx, odt), il faut utiliser la version d'OTX compatible avec la version du schéma TEI. 



Compatibilité des versions
=========================================

+-------------------+-----------------------+----------------------+-----------------+
| TEI OpenEdition   | Modèle éditorial OJ   |Modèle éditorial OB   | OTX             |
+===================+=======================+======================+=================+
| 1.6.2             | 1.0.1                 | 1.0.1                | v1.2.0          |
+-------------------+-----------------------+----------------------+-----------------+
| 1.6.1             | 1.0.0                 | 1.0.0                | v1.1.2          |
+-------------------+-----------------------+----------------------+-----------------+


- `Modèle éditorial OpenEdition Journals <https://github.com/OpenEdition/oej.em/releases>`_
- `Modèle éditorial OpenEdition Books <https://github.com/OpenEdition/oeb.em/releases>`_
- `OTX <https://github.com/OpenEdition/OTX/releases>`_

