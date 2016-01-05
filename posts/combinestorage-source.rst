.. title: CombineStorage source
.. slug: combinestorage-source
.. date: 2014-06-25 16:04:42 UTC+13:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text

    I just added a new source actor: 

      CombineStorage 

    This source works similar to the CombineVariables source, as it allows 
    you to combine string representations of storage items ("%{name}") and 
    variables ("@{name}") into a single string. 

  Furthermore, I added the ExpandVariables and ExpandStorage 
  transformers which expand the variables and/or storage items (using 
  the string representations) in the strings passing through. 
