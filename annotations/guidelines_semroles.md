## Annotation of semantic roles

Select one of the two **semantic roles** annotation projects:
  * Bad quality OCR: semroles
  * Good quality OCR: semroles

#### What to annotate
We are interested in the **semantic roles** in sentences (i.e. the role that the arguments of a predicate take in an event), and in particular:
  * the verb,
  * for each verb, its semantic roles:
    * _Agent_: The doer, or instigator of the action denoted by the predicate
    * _Patient_: The undergoer of the action or event denoted by the predicate
    * _Theme_: The entity that is moved by the action or event denoted by the predicate
    * _Experiencer_: The living entity that experiences the action or event denoted by the predicate
    * _Goal_: The location or entity in the direction of which something moves
    * _Benefactive_: The entity that benefits from the action or event denoted by the predicate
    * _Source_: The location or entity from which something moves
    * _Instrument_: The medium by which the action or event denoted by the predicate is carried out
    * _Locative_: The specification of the place where the action or event denoted by the predicate is situated

Different people are likely to annotate things in this task, and these differences are very valuable, as we can see how different disciplines may think of agency differently.

#### Questions and answers

Link to Questions and answers with examples, and a more detailed description of each semantic role [here](https://docs.google.com/document/d/1NLenqdv-mD298XVLs3LTUmebLBAgcaAzlGYaFLmH-LM/edit).
  
#### How to annotate
* On the RHS column, make sure you have selected the Layer `SemRoles` (if you don't see it, make sure you are in an 'semroles' project).
* Select with the mouse the span of text you want to annotate, and select the role from the `argument` drop-down menu. Try to annotate the full verb (e.g. `will destroy` instead of just `destroy`), and to annotate the full noun phrase in the case of the semantic roles (e.g. `the thrashing machine` instead of `thrashing machine`).
* For each semantic role (agent, patient, theme, etc) add a relation pointing to its related verb: to do this click on the annotation of the semantic role and drag the mouse until the correct `verb` annotation.
* To delete a relation: click on the `(DSRL)` relation tag you want to delete, and click on `Delete` in the Annotation box on the RHS column.
* To delete an annotation: click on the annotation you want to delete, and click on `Delete` in the Annotation box on the RHS column.
* There is a `comment` box for each annotation of a semantic role: please write any doubt, idea, complain, suggestion, etc in this box.
* If there is no verb or nothing to annotate in the whole file, just click on "Workflow>finish" and go to the next article ("Document>Next").

![See example here](https://github.com/mcollardanuy/lwm_playground/blob/master/annotations/semrolesGood.png)
