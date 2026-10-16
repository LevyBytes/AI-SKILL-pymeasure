# Adding instruments

Adding an instrument under `pymeasure.instruments` is a valuable way to improve PyMeasure. Even a driver with only a small feature set can unblock later work, because other users may need the same model.

Before you start, read the PyMeasure [contributing work-flow](https://pymeasure.readthedocs.io/en/latest/dev/contribute.html), which explains how to add a development-version feature such as a new instrument.

Pymeasure instruments talk to devices by sending bytes, either raw or as ASCII characters encoded into bytes. [property creators](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/properties.html#properties) make python properties easier to define; [channels](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/channels.html#channels) provide a similar helper path for channel implementations. Use [tests](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/tests.html#tests) to keep the implementation maintainable and smoother to evolve.

The sections below outline the expected layout for instrument code.

- [File structure](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/instrument.html)
  - [Changing the init file](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/instrument.html#updating-the-init-file)
  - [Add test files](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/instrument.html#add-test-files)
  - [Adding documentation](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/instrument.html#adding-documentation)

- [Instrument file](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/instrument.html#instrument-file)
- [User-facing interface for your instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/instrument.html#your-instrument-s-user-interface)
  - [Common instrument types](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/instrument.html#common-instrument-types)
  - [Handling status codes and indicator values](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/instrument.html#managing-status-codes-or-other-indicator-values)

- [Defining default connection settings](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/instrument.html#defining-default-connection-settings)
  - [Single interface](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/instrument.html#single-interface)
  - [Multiple interfaces](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/instrument.html#multiple-interfaces)

- [Writing properties](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/properties.html)
  - [Property factory helpers](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/properties.html#the-property-factories)
  - [Validator-based value restrictions](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/properties.html#restricting-values-with-validators)
  - [Mapping values](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/properties.html#mapping-values)
  - [Boolean properties](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/properties.html#boolean-properties)
  - [Processing values before setting them](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/properties.html#processing-of-set-values)
  - [Processing values returned by the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/properties.html#processing-of-return-values)
  - [Checking the instrument error state](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/properties.html#checking-the-instrument-for-errors)
  - [Working with multiple values](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/properties.html#using-multiple-values)
  - [Dynamic properties](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/properties.html#dynamic-properties)

- [Sharing behavior across similar instruments](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/properties.html#instruments-with-similar-features)
  - [Instrument families with differing parameter values](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/properties.html#instrument-family-with-different-parameter-values)
  - [Sharing command syntax across instruments](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/properties.html#instruments-with-similar-command-syntax)

- [Channel-based instruments](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/channels.html)
  - [Creating a channel with `ChannelCreator`](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/channels.html#adding-a-channel-with-channelcreator)
  - [Creating multiple channels with `MultiChannelCreator`](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/channels.html#adding-multiple-channels-with-multichannelcreator)
  - [Advanced channel management](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/channels.html#advanced-channel-management)

- [Advanced communication protocols](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/advanced_communication.html)
  - [Instrument’s inner workings](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/advanced_communication.html#instrument-s-inner-workings)
  - [Adding device addressing and delay handling](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/advanced_communication.html#adding-a-device-address-and-adding-delay)
  - [Bytes communication](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/advanced_communication.html#bytes-communication)

- [Writing tests](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/tests.html)
  - [Protocol tests](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/tests.html#protocol-tests)
  - [Device tests](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/tests.html#device-tests)

- [Implementation-challenge solutions](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/solutions.html)
  - [General issues](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/solutions.html#general-issues)
  - [Communication protocol issues](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/solutions.html#communication-protocol-issues)
  - [Channels](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/solutions.html#channels)
