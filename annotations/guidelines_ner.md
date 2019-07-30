## Annotation of entities
Choose the project, either:
  * Bad quality OCR: entities, or
  * Good quality OCR: entities

#### What to annotate

We are interested in the following entities:

    * Persons (`PER`): proper nouns referring to people.
    * Locations (`LOC`): places that can be located in a map.
    * Organisations (`ORG`): proper nouns referring to organisations.
    * Machine objects (`MOBJ`): physical machines.

#### How to annotate
* On the RHS column, make sure you have selected the Layer `custom_ent` (if you don't see it, make sure you are in an 'entities' project).
* Select with the mouse the span of text you want to annotate as an entity (or double-click on the word, if want to annotate just one word).
* Change the value to the correct annotation (`PER` for people, `LOC` for locations, `ORG` for organisations, `MOBJ` for machine objects).
* If you want to delete an annotation, click on the annotation that you want to delete and click on "Delete" on the RHS column.

![See example here](https://github.com/alan-turing-institute/Living-with-Machines/blob/master/working_documents/labs/language/mro_subgroups/annotation/nerGood.png)
