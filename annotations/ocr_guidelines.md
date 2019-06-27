# Guidelines: annotations of the OCR subsamples

## Accessing the annotation tool

1. Send an email to Daniel vS and Mariona, we will send you your credentials and range of articles you can annotate (that does not mean you have to annotate them all! It's just to minimise overlap).
2. Go to `http://52.151.66.55:8080/login.html`.
3. Enter your login credentials.

## Annotation process

1. Select the project, either "Annotation of bad quality OCR articles" or "Annotation of good quality OCR articles"
2. Click on "Annotation" tab from the left hand side column.
3. Select the first article from the range of articles we've suggested, and click on "Open".
  * A file name in black means that the article has never been opened by you.
  * A file name in blue means that you have opened the file, and maybe started annotating it.
  * A file name in red means that you have completed the annotation (see point 7).
4. Recommended: go to "Settings" and change "Page size" to 200.
5. Annotate the article (see section below: "How to annotate")
6. Click on "Page > Next" to go to the second page of the article, if needed.
7. If you are sure you have annotated everything you wanted to annotate from the article, then you can click on "Finish". Please note that if you click on "Finish" you won't be able to annotate the file again. Write to Daniel, Giorgia, or Mariona to open this article again.
8. Click on "Document > Next" to go to the next article to annotate.

## What to annotate

### Entities

We are interested in the following entities:
  * Persons (`PER`): proper nouns referring to people.
  * Locations (`LOC`): places that can be located in a map.
  * Organisations (`ORG`): proper nouns referring to organisations.
  * Machine objects (`MOBJ`): physical machines.

### Semantic relations

If a sentence contains machine objects, we are also interested in the **semantic roles* of this sentence, and in particular:
  * every verb that is an action verb in the sentence.
  * for each verb, its agent (the cause or initiator of the action) if there is one.
  * for each verb, its patient (the target or undergoer of the action) if there is one.

#### Examples

* **Sentence:** "Machines will destroy us".
  * Agent: `machines`
  * Patient: `us`
  * Verb: `will destroy`

* **Sentence:** "With a spinning jenny a worker could spin several threads at once".
  * Agent: `a worker`
  * Patient: `several threads`
  * Verb: `could spin`

## How to annotate

### Entities
* On the RHS column, select "Layer: `custom_ent`".
* Select with the mouse the span of text you want to annotate as an entity (or double-click on the word, if the entity consists of just one word.
* Change the value to the correct annotation (`PER` for people, `LOC` for locations, `ORG` for organisations, `MOBJ` for machine objects).

### Semantic relations
* On the RHS column, select "Layer: `sem_roles`".
* Select with the mouse the span of text you want to annotate as either `verb`, `agent` or `patient`, from the argument drop-down menu. Try to annotate the full verb (e.g. `will destroy` instead of just `destroy`), and to annotate the full noun phrase in the case of the `agent` and the `patient` (e.g. `the thrashing machine` instead of `thrashing machine`).
* Click on the `patient` or the `agent` annotations and drag the mouse until the annotation of the `verb`.
