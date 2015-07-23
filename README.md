ModestXively
============

This is a memory efficient version of ERxPachube library (https://code.google.com/p/pachubelibrary/) for Pachube/Cosm/Xively GET and PUT API communication.


RAM efficiency is achieved by not preparing the whole message in RAM before sending it. The problem is that the size of the message body must be known before it is sent. To avoid having to prepare the whole message to know its size a fixed pre estimated size is sent instead. Then the message is generated and directly sent character by character while they are created thus not taking up any memory. Finally, to keep the anounced message size, the message is padded with blanks until the size is reached.

This has two drawbacks: first, a fixed size must be chosen that will not be exeeded by the message under all circumstances. Secondly, Time is wasted by having to send the padding blanks. But the memory saving is considrable and the upper bound of the message size can be estimated relatively easy.

With this method the maximum number of streams could be increased from 5 to 32. 

This library also adds the possibility to extract the current time from the HTTP header.