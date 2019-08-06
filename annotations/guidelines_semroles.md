## Annotation of semantic roles

Select one of the two **semantic roles** annotation projects:
  * Bad quality OCR: semroles
  * Good quality OCR: semroles

#### What to annotate
We are interested in the **semantic roles** in sentences, and in particular in those sentences about machines.

In this [document](https://docs.google.com/document/d/1NLenqdv-mD298XVLs3LTUmebLBAgcaAzlGYaFLmH-LM/edit) there is an up-to-date description and instructions of the annotation task, and contains a section on questions and answers that have come up so far. Feel free to add more questions and examples at the end of the document.
  
#### How to annotate
* On the right-hand side column, make sure you have selected the Layer `SemRoles` (if you don't see it, make sure you are in a 'semroles' project).
* Select with the mouse the span of text you want to annotate, and select the role from the `argument` drop-down menu. Try to annotate the full verb (e.g. `will destroy` instead of just `destroy`), and to annotate the full noun phrase in the case of the semantic roles (e.g. `the thrashing machine` instead of `thrashing machine`).
* For each semantic role (agent, patient, theme, etc) add a relation pointing to its related verb: to do this click on the annotation of the semantic role and drag the mouse until the correct `verb` annotation.
* To delete a relation: click on the `(DSRL)` relation tag you want to delete, and click on `Delete` in the Annotation box on the right-hand side column.
* To delete an annotation: click on the annotation you want to delete, and click on `Delete` in the Annotation box on the RHS column.
* There is a `comment` box for each annotation of a semantic role: please write any doubt, idea, complain, suggestion, etc in this box.
* If there is no verb or nothing to annotate in the whole file, just click on "Workflow>finish" and go to the next article ("Document>Next").

![See example here](https://github.com/mcollardanuy/lwm_playground/blob/master/annotations/semrolesGood.png)
