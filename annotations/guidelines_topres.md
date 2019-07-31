## Toponym resolution annotations

This document contains the annotation guidelines for marking up and georeferencing locations mentioned in unstructured historical texts. The task of the annotator is to recognize each location mentioned in the text and map it to the URL of the Wikipedia article that refers to it.

Select a `Toponym resolution: batch X` project.

### The task

The task of toponym resolution is in a way very similar to word sense disambiguation in that the most common sense is in most cases the correct sense. However, place names are often highly ambiguous, and it is our intention to tackle the problem of the disambiguation where the most common sense approach does not work. There are, for instance, more than 20 different places named Paris all over the world. As is usually the case in any sense disambiguation task, most of the instances are expected to correspond to the most relevant sense and, thus, to be quite straightforward to annotate. Instances like 'Paris' or 'London' will occur often and will, with some rare exceptions, always refer to the same entity (capital of France and England respectively). Nevertheless, due to the nature of this experiment, it is of the utmost importance that less usual cases (such as 'London' referring to a city of Ontario, Canada) are correctly identified.

### What to annotate

Location: any named entity that is static and can be defined according to its pair of static world coordinates (including metonyms, as in 'France signed the deal.'). If there is an OCR error, we annotate the location anyway if we can recognise it (see example below).

### How to annotate

The task of the annotator is to map each location found in the text with the URL of the Wikipedia article that refers to it.

To do so:
* On the RHS column, make sure you have selected the Layer `Custom entity` (if you don't see it, make sure you are in an 'Toponym resolution' project).
* Select with the mouse the span of text you want to annotate (e.g. 'West Laviogton') and select `LOCWiki` from the dropdown menu.
* Other annotation types:
  * `BUILDING`: Names of buildings (e.g. schools, hospitals, factories, etc.). Optional to link to Wikipedia article if it exists.
  * `STREET`: Streets and neighbourhoods. Optional to link to Wikipedia article if it exists.
  * `ALIEN`: Extraterrestrial locations (e.g. the moon). Optional to link to Wikipedia article if it exists.
  * `ADJ`: Adjectival and demonymic forms of place names (e.g. German wine, the French, etc.). No link to Wikipedia.
  * `OTHER`: Others, as in famous trees (https://en.wikipedia.org/wiki/Lone_Cypress). Optional to link to Wikipedia article if it exists.
  * `UNKNOWN`: If the location has no Wikipedia entry. No link to Wikipedia.
  * `FICTION`: If it is a fictional/mythical place (e.g. Lilliput). Optional to link to Wikipedia article if it exists.
* If selected tag is `LOCWiki`:
  * Go to Wikipedia (English version)
  * Find the correct article corresponding to the place mentioned in the text (e.g. `https://en.wikipedia.org/wiki/West_Lavington,_Wiltshire`).
  * Copy the full URL and paste it to the identifier box.
* To delete an annotation, click on it and click on `Delete` in the Annotation box in the RHS column.

The article title will give you an indication of the place of publication of the article, to help you disambiguate the toponyms in the article (e.g. `10713959_Dorchester1820.txt` is an article published in Dorchester, Dorset, in the 1820s).

### Working with historical texts

Working with historical texts poses some extra challenges to those inherent to the task of toponym resolution:
* **Locations that do not exist (as such) anymore:** such as Prussia, a former kingdom in north-central Europe, Waterloo and Hohenfriedberg, critical battlegrounds, or Wasgenwald, a former region that encompassed the two adjacent regions of the Vosges and Wasgau.
* **Locations that have changed their name:** such as Petrograd and Leningrad, now known as St. Petersburg, Edo, now known as Tokyo, or the once capital of Prussia Köningsberg, now a Russian city called Kaliningrad.
* **Graphic variation:** which can be of two kinds: historical or OCR-induced. Historical name change includes these cases in which locations have undergone ortographic variation throughout history (this might also be due to lack of standardization in transliterating or translating foreign locations), such as the in Dutch 'Dusseldorp', name used in former times to refer to the German city of Düsseldorf, or in English 'Marseilles' to refer to the French city of Marseille. Using historical texts means most of the times working with OCR material. Examples of OCR-induced graphic variation of locations are 'Luxernbourg' instead of 'Luxembourg' and 'St. Vifh' instead of 'St. Vith'.

Besides, the collections of text that we have are considerably regional. This adds difficulty to the disambiguation task. The more universal a text is, the more we can expect a general reader to know all the entities that are mentioned in it. The more regional a text is, the less a general reader is likely to know the mentioned entities. To illustrate this with an example, a reader of the St. Vither Volkzeitung, a newspaper issued in St. Vith, a German-speaking Belgian municipality, encountering the word 'Born' in a piece of news will know it to refer to the little village which is 7 kilometers away from St. Vith, and not to the homonym Dutch and Luxemburguish municipalities or the homonym neighborhood in Barcelona.


### Example

![Example](https://github.com/mcollardanuy/lwm_playground/blob/master/annotations/topres.png)
