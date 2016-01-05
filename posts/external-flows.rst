.. title: External flows
.. slug: external-flows
.. date: 2014-06-27 14:01:41 UTC+13:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text

Some major changes have happened to external flows.

* In the past, when externalizing flow snippets, the actors had to be wrapped
  in an InstantiatableStandalone/Source/Transformer/Sink. This requirement was
  historical (only introduced an additional layer of complexity) and has now been
  removed, as well as the InstantiatableStandalone/Source/Transformer/Sink
  actors. These no-longer available actors will get replaced automatically with
  sensible actors (Standalones/SequenceSource/SubProcess/Sequence) in order no to
  break any existing external flows. 

* I introduced a range of new actors to the adams-meta module for loading
  external actors: IncludeExternalStandalone/Source/Transformer/Sink. In contrast
  to the External... actors in the adams-core module, these replace themselves
  with actual external flow snippet the first time the flow gets setup. This is
  the more efficient way of using external flows if there is no need for
  variables attached to the flow file option.
