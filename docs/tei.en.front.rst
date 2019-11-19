.. _tei-en-front:

text/front
##############################################

.. contents:: Summary
   :depth: 2

.. _tei-en-teifront-resume:

Abstracts
=============================================

**Xpath**

Abstracts: ``/TEI/text/front/div[@type='abstract' and @xml:lang]``


**Use recommandations**

- the ``xml:lang`` attribute is required with a value in ISO 639-1 format;
- single paragraph, line break allowed (``<lb>`` tag);
- no references to notes.

**Example**

.. code-block:: xml

   [...]
   <text>
       <front>
   [...]
           <div type="abstract" xml:lang="fr">
               <p>Il était sur le dos, un dos aussi dur qu’une carapace, et, en relevant un peu la tête, il vit, bombé, brun, cloisonné par des arceaux plus rigides, son abdomen sur le haut duquel la couverture, prête à glisser tout à fait, ne tenait plus qu’à peine. Ses nombreuses pattes, lamentablement grêles par comparaison avec la corpulence qu’il avait par ailleurs, grouillaient désespérément sous ses yeux. « Qu’est-ce qui m’est arrivé ? » pensa-t-il.</p>
               <p>Ce n’était pas un rêve. [...]</p>
           </div>
           <div type="abstract" xml:lang="en">
               <p>"Oh, God", he thought, "what a strenuous career it is that I've chosen! Travelling day in and day out. Doing business like this takes much more effort than doing your own business at home, and on top of that there's the curse of travelling, worries about making train connections, bad and irregular food, contact with different people all the time so that you can never get to know anyone or become friendly with them. It can all go to Hell! "He felt a slight itch up on his belly; pushed himself slowly up on his back towards the headboard so that he could lift his head better; found where the itch was, and saw that it was covered with lots of little white spots which he didn't know what to make of; and when he tried to feel the place with one of his legs he drew it quickly back because as soon as he touched it he was overcome by a cold shudder. He slid back into his former position. "Getting up early all the time", he thought, "it makes you stupid. You've got to get enough sleep. Other travelling salesmen live a life of luxury. For instance, whenever I go back to the guest house during the morning to copy out the contract, these gentlemen are always still sitting there eating their breakfasts. I ought to just try that with my boss; I'd get kicked out on the spot. But who knows, maybe that would be the best thing for me. If I didn't have my parents to think about I'd have given in my notice a long time ago, I'd have gone up to the boss and told him just what I think, tell him everything I would, let him know just what I feel. He'd fall right off his desk! And it's a funny sort of business to be sitting up there at your desk, talking down at your subordinates from up there, especially when you have to go right up close because the boss is hard of hearing. Well, there's still some hope; once I've got the money together to pay off my parents' debt to him - another five or six years I suppose - that's definitely what I'll do. That's when I'll make the big change.</p>
           </div>
           <div type="abstract" xml:lang="es">
               <p>Las preocupaciones son mucho mayores cuando se trabaja fuera, por no hablar de las molestias propias de los viajes: estar pendiente de los enlaces de los trenes; la comida mala, irregular; relaciones que cambian constantemente, que nunca llegan a ser verdaderamente cordiales, y en las que no tienen cabida los sentimientos. amsa era viajante de comercio-, y de la pared colgaba una estampa recientemente recortada de una revista ilustrada y puesta en un marco dorado.</p>
           </div>
   [...]


.. _tei-en-teifront-oeuvres:

Reading notes and reviews
===================================================


**Xpath**

| Title of the reviewed work: ``/TEI/text/front/div[@type='review']/p[@rend='review-title']``
| Author of the reviewed work: ``/TEI/text/front/div[@type='review']/p[@rend='review-author']``

| Bibliographical notice of the reviewed work: ``/TEI/text/front/div[@type='review']/p[@rend='review-bibliography']``

| Publication date of the reviewed work: ``/TEI/text/front/div[@type='review']/p[@rend='review-date']``

**Use recommandations**

- each document must contain a single review or reading note;
- they should not be entitled “Reading notes”;
- The document should also be given a title, recommanded format : Author of the reviewed work, *Title of the reviewed work*;
- possibility to add bibliographical elements (publisher, place and year of publishing…) as a “subtitle”;
- rewiews metadata offers the possibility to create specific indexes on the journal website.

**Example**

.. code-block:: xml

   [...]
   <text>
       <front>
   [...]
           <div type="review">
               <p rend="review-title">La métamorphose</p>
               <p rend="review-author">Franz Kafka</p>
               <p rend="review-bibliography">Franz Kafka, <hi rend="italic">La métaporphose</hi> [1938] , trad. de l'allemand par Alexandre Vialatte, 224 pages, 140 x 205 mm. Collection Du monde entier, Gallimard-nouv. ISBN 2070235157.</p>
               <p rend="review-date">1938</p>
           </div>
   [...]


.. _tei-en-teifront-notes:

Author notes, editors notes, errata, acknowledgements
================================================================

**Xpath**

| Author notes: ``/TEI/text/front/note[@resp='author']/p``
| Editor notes: ``/TEI/text/front/note[@resp='editor']/p``
| Erratum: ``/TEI/text/front/div[@type='correction']/p``
| Dedications: ``/TEI/text/front/div[@type='dedication']/p``
| Acknowledgements:``/TEI/text/front/div[@type='ack']/p``

**Use recommandations**

- several paragraphs allowed;
- line break allowed (``<lb>`` tag).

*Example*:

.. code-block:: xml

   [...]
   <text>
       <front>
   [...]
           <div type="ack">
               <p>Je remercie le site Blind Text Generator qui a fourni tout le faux-texte de ce document.</p>
           </div>
           <div type="correction">
               <p>L'erratum permet de signaler les modifications apportées au texte après sa publication.</p>
           </div>
           <note resp="editor">
               <p>
                   Le texte de ce document a été généré sur le site <ref target="http://www.blindtextgenerator.com/">http://www.blindtextgenerator.com</ref>.
               </p>
           </note>
           <note resp="author">
               <p>
                   Les résumés français, anglais et espagnol sont des extraits de <hi rend="italic">La Métamorphose</hi> de Franz Kafka.
               </p>
           </note>
       </front>
   [...]

