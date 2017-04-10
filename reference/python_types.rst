Mapping NStack types to Python types
------------------------------------

============== ============================ 
NStack Type    Python Type                
============== ============================ 
``Integer``    ``int``              
``Double``     ``double.Double``  
``Boolean``    ``bool``  
``Text``       ``str``   
Tuple          ``tuple``    
Struct         ``collections.namedtuple`` *
Array          ``list``                  
Sum            see section below         
``[Byte]``     ``bytes``                  
``x optional`` ``None`` or x              
============== ============================

\* you can return a normal tuple (see struct section below)

Sum Types
---------

Using sum types
::

  type URL = Text;
  type Referrer = URL;
  type Target = URL;
  type Event = PageImpression URL | Click (Referrer, Target);

blah blah blah ::

  class Event(object):
    ...
    class PageImpression(Event):
      ...
    class Click(Event):
      ...

  
sfdsf

.. code:: python

  ex_impression = nstack.Event.PageImpression("http://www.nstack.com/")
  ex_click = nstack.Event.PageImpression(("http://www.nstack.com/", "http://demo.nstack.com/"))

dsfsdf ::

  >> isinstance(ex_impression, nstack.Event)
  True
  >> isinstance(ex_impression, nstack.Event.PageImpression)
  True
  >> isinstance(ex_impression, nstack.Event.Click)
  False

sdfsdfd

.. code:: python

  if isinstance(v, nstack.Event.PageImpression):
    ... # do something with a page impression
  elif isinstance(v, nstack.Event.Click):
    ... # do something with a click
    
sdfsdfsd ::

  >> ex_impression.value
  "http://www.nstack.com/"
  >> ex_click.value
  ("http://www.nstack.com/", "http://demo.nstack.com/")
  >> ex_impression.getPageImpression()
  "http://www.nstack.com/"
  >> ex_impression.getClick()
  Traceback (most recent call last):
    File "<stdin>", line 1, in <module>
  TypeError: Not a Click
  >> ex_impression.match(lambda i: "got a page impression",
                         lambda i: "got a click")
  "got a page impression"
    
Structs
-------

::

  type URL = Text;
  type Event = PageImpression URL | Click { referrer: URL, target: URL };
  
sfsdfsdf ::

  ClickData = collections.namedtuple("ClickData", ["referrer", "target"])

ssdfsdf ::

  >> # input = nstack.Event.Click(("http://www.nstack.com/", "http://demo.nstack.com/")) 
  >> input.getClick().referrer
  "http://www.nstack.com/"
  >> input.getClick().target
  "http://demo.nstack.com/" 
