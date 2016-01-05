.. title: Get Started - Extending
.. slug: dev-get-started-extending
.. date: 2015-12-18 14:46:52 UTC+13:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text
.. author: FracPete

.. contents::

What do you need to do to create a new actor? Not much, simply create a new
class and add a 16x16 icon for this actor. That's it!

The following sections will guide you through the process of implementing your
first actor.

The class
---------

In the example here, we will be implementing a simple transformer that can take
integers, doubles and numbers in string representation. This transformer then
adds the number 42 to them and forwards the result for further processing.


Picking the superclass
----------------------

The four types of actors in ADAMS, standalone, source, transformer and sink,
are determined by two interfaces, depending on whether input is accepted
and/or output is generated:

* ``adams.flow.core.InputConsumer`` (transformer, sink)
* ``adams.flow.core.OutputProducer`` (source, transformer)

But you don't have to implement these interfaces yourself, there are already
some abstract superclasses that you can directly derive from:

* ``adams.flow.standalone.AbstractStandalone``
* ``adams.flow.source.AbstractSource``
* ``adams.flow.transformer.AbstractTransformer``
* ``adams.flow.sink.AbstractSink``

Thanks to ADAMS' dynamic class discovery, you only have to place your classes
in the same package as these abstract superclasses. If you want to use a
different class hierarchy, you have to let ADAMS know about in form of a
properties file. For instance, for developing our new transformer, called
``org.awesome.transformer.Funky``, you have to create a file called
``ClassLister.props`` in the ``adams.core`` package with the following content:

.. code:: properties

   adams.flow.core.AbstractActor=\
     org.awesome.transformer

Ultimately, all actors are derived from ``adams.flow.core.AbstractActor``, hence
you need ADAMS let know in which packages to look for them.


Documentation
-------------

In order to keep documentation relevant and avoid duplication, it is placed
directly into the code. Each actor has a ``globalInfo`` method returning the
main description in the help available in the GUI.

In our example, the the method would look like this:

.. code:: java

   public String globalInfo() {
     return "Our funky transformer. Adds 42 to incoming data.";
   }


Input and output
----------------

Before a flow is executed, ADAMS checks whether the actors are actually
compatible with each other. For this **static type check**, InputConsumers have
an ``accepts()`` method and OutputProducers a ``generates()`` one, each return
an array of classes.

Our *Funky* transformer is supposed to take integers, doubles and strings. In
other words, the ``accepts()`` method looks like this:

.. code:: java

   public Class[] accepts() {
     return new Class[]{Integer.class, Double.class, String.class};
   }

As output, the transformer only generates doubles. Here is the corresponding
``generates()`` method:

.. code:: java

   public Class[] generates() {
     return new Class[]{Double.class};
   }

Any actor that outputs numbers (e.g., ``adams.flow.source.RandomNumberGenerator``)
or strings (e.g., ``adams.flow.source.StringConstants``), will be compatible with
our transformer.


Processing data
---------------

Since the handling of documentation and compatibility is covered, we can concentrate on the actual processing of the data.

The life cycle of an actor is as follows:

1. ``setUp()`` (initialization)
2. ``execute()`` (called with each token passing through, in case of transformers)
3. ``wrapUp()`` (called after flow finishes)
4. ``destroy()`` (for freeing up memory, etc.)

The ``execute()`` is just a wrapper around the following three methods:

1. ``preExcecute()``
2. ``doExcecute()``
3. ``postExcecute()``

In our case, only the ``doExecute()`` method needs to be implemented, as it is the
only that is abstract. The others perform other duties, like debugging output
of the size of the actor before/after the ``doExecute()`` call for tracking memory
leaks.

Data gets passed around in the flow as tokens and the container class dealing
with it is ``adams.flow.core.Token`` (the actual data is its payload). The
``AbstractTransformer`` class already contains a member variable for the input,
``m_InputToken``, and one for the output, ``m_OutputToken``.
Leaving the output token at null stops the execution of any actor following
ours. We will be using this approach in case we encounter a string that we
can't parse as a double.  The ``doExecute()`` method also returns string, which is
used to return error messages (``null`` if everything is fine). If we have a valid
number, we add 42 to it.

Here is the code processing the data:

.. code:: java

   protected String doExecute() {
     String result = null;
     Number number = null;
     if (m_InputToken.getPayload() instanceof String) {
       try {
         number = new Double((String) m_InputToken.getPayload());
       } catch (Exception e) {
         number = null;
         result = "Failed to parse input string '" + m_InputToken.getPayload() + "' as number: " + e;
       }
     }
     else {
       number = (Number) m_InputToken.getPayload();
     }
     if (number != null)
       m_OutputToken = new Token(number.doubleValue() + 42.0);
     return result;
   }


The full implementation
-----------------------

And here is the full implementation of our transformer:

.. code:: java

   package adams.flow.transformer;
   
   import adams.flow.core.Token;
   
   public class Funky extends AbstractTransformer {
     public String globalInfo() {
       return "Our funky transformer. Adds 42 to incoming data.";
     }
     public Class[] accepts() {
       return new Class[]{Integer.class, Double.class, String.class};
     }
     public Class[] generates() {
       return new Class[]{Double.class};
     }
     protected String doExecute() {
       String result = null;
       Number number = null;
       if (m_InputToken.getPayload() instanceof String) {
         try {
           number = new Double((String) m_InputToken.getPayload());
         } catch (Exception e) {
           number = null;
           result = "Failed to parse input string '" + m_InputToken.getPayload() + "' as number: " + e;
         }
       }
       else {
         number = (Number) m_InputToken.getPayload();
       }
       if (number != null)
         m_OutputToken = new Token(number.doubleValue() + 42.0);
       return result;
     }
   }

Option handling
---------------

Though not necessary for this example, I will still cover briefly how option
handling works in ADAMS.

Each option that is to be available through the user interface, needs to
implement a **get**, a **set** and a **tool-tip** method. The latter contains the
documentation for the option.

In our transformer example, we might want to make the actor a bit more flexible and allow the user to choose and increment different from 42. We could call the option (or property in Java Beans terms) *increment*. This will result in the following three methods:

* ``getIncrement()``
* ``setIncrement(double)``
* ``incrementTipText()``

Now we have to register this property with the actor as an option, in order to
make it accessible in the user interface. This happens in the methdo
``defineOptions()``, by adding an option description to the option manager. This
description includes the command-line string of the option, the Bean property
name and the default value. For numeric values you can also describe lower and
upper bounds. We don't need really need bounds, but for demonstration purposes,
we only want to allow positive values or zero:

.. code:: java

   public void defineOptions() {
     super.defineOptions();
     m_OptionManager.add(
       "inc", "increment",
       42.0, 0.0, null);
   }

One more important thing to mention: each ``set`` method for an option needs to
call the ``reset()`` method. This call signals the actor that the options have
changed and the current state is no longer valid.

The complete actor code now looks like this:

.. code:: java

   package adams.flow.transformer;
   
   import adams.flow.core.Token;
   
   public class Funky extends AbstractTransformer {
     protected double m_Increment;
     public String globalInfo() {
       return "Our funky transformer.";
     }
     public void defineOptions() {
       super.defineOptions();
       m_OptionManager.add(
         "inc", "increment",
         42.0, 0.0, null);
     }
     public void setIncrement(double value) {
       if (getOptionManager().isValid("increment", value)) { // checks bounds for numeric options
         m_Increment = value;
         reset();
       }
     }
     public double getIncrement() {
       return m_Increment;
     }
     public String incrementTipText() {
       return "The amount to add to the incoming values.";
     }
     public Class[] accepts() {
       return new Class[]{Integer.class, Double.class, String.class};
     }
     public Class[] generates() {
       return new Class[]{Double.class};
     }
     protected String doExecute() {
       String result = null;
       Number number = null;
       if (m_InputToken.getPayload() instanceof String) {
         try {
           number = new Double((String) m_InputToken.getPayload());
         } catch (Exception e) {
           number = null;
           result = "Failed to parse input string '" + m_InputToken.getPayload() + "' as number: " + e;
         }
       }
       else {
         number = (Number) m_InputToken.getPayload();
       }
       if (number != null)
         m_OutputToken = new Token(number.doubleValue() + m_Increment);
       return result;
     }
   }

**One final note:** instead of using ``System.out`` and ``System.err``, actors
should use ``getSystemOut()`` and ``getSystemErr()`` for output on the console.
By doing this, output from stdout and stderr gets captured by ADAMS' logging
facility.  Debugging output can be output using for instance ``debug(String)``.

The icon
--------

As for the icon that goes with the actor, it is simple a GIF, PNG or JPG image
with the same filename as the actor, placed in the ``adams.gui.images`` package.
For instance, using our ``org.awesome.transformer.Funky`` transformer example, you
could create a file called ``org.awesome.transformer.Funky.gif``, using one of
these templates:

* ``adams.flow.standalone.Unknown.gif``
* ``adams.flow.source.Unknown.gif``
* ``adams.flow.transformer.Unknown.gif``
* ``adams.flow.sink.Unknown.gif``

.. raw:: html

   The templates already contain a frame with the color associated with the type
   of actor: <font color="red">standalone</font>, <font color="orange">source</font>, 
   <font color="green">transformer</font> and <font color="grey">sink</font>.

