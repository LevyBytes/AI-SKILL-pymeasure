# pymeasure.instruments.comedi.readAI

pymeasure.instruments.comedi.readAI(*device*, *channel*, *range=None*, *count=1*)

Read a single measurement (count==1) from the analog input channel of the specified device. Multiple readings can be performed when count is not one; those readings are separated by an arbitrary time
