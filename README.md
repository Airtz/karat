# ![](res/karat.webp) karat

<p align=center>In-game spam filter for Dofus. Named after the Meridia of tranquility.</p>

<p align=center>Windows only.</p>

<p align=center><a href="https://donate.stripe.com/7sI6rK74C7Wk2C46oo"><img src="https://github.com/Airtz/karat/blob/main/res/support.png" width=110 height=132/></a></p>

## Getting started

1. [Download](https://downgit.github.io/#/home?url=https://github.com/Airtz/karat/tree/main/bin) `karat` binaries from the `bin` directory
2. Launch your Dofus client(s)
3. Load your character(s)
4. Launch `karat.exe`

## In-game commands

<p align=center><img src="https://github.com/Airtz/karat/blob/main/res/chat.png"/></p>

Input must be prefixed with `$`. Availables commands are:

* `help` - show this message
* `load` &lt;path&gt; - load a classifier from the specified path
* `mode` &lt;log|filter|learn&gt; - set the operating mode
* `save` &lt;path&gt; - save the current classifier to the specified path
* `threshold` &lt;value&gt; - set the current classifier threshold
* `train` - open the training UI

## Operating modes

* `log`
   * log incoming messages for manual classification
* `filter` (default)
   * log incoming messages for manual classification
   * filter incoming messages using the current classifier
* `learn`
   * log incoming messages for manual classification
   * filter incoming messages using the current classifier
   * automatically train the current classifier

Switching to `learn` mode is not recommended with low accuracy classifiers.

## Threshold

Filtering is done using a Multinomial Naive Bayes Classifier with the following decision rule:

<p align=center><img src="https://github.com/Airtz/karat/blob/main/res/decision.png"/></p>

With `p` the estimated probability of message `m` being a spam, `t` the classifier threshold and `S` the spam set.

Default value for `t` is 0.8.

## Training the classifier

If the accuracy of the provided classifier is not good enough, you can train your own.

Open the training UI using the `train` command and manually classify messages as spams or hams using move buttons then hit the train and retrieve button. Repeat until the accuracy is good enough.

<p align=center><img src="https://github.com/Airtz/karat/blob/main/res/ui.png"/></p>

1. Spam list
    * `Channel`: channel in which the message was sent
    * `Sender`: name of the sender
    * `p`: estimated probability of the message being a spam
3. Ham (non-spam) list
4. Train the classifier to classify listed spams and hams as such and then retrieve the current log
5. Move selected ham to the spam list (you can also double click on the item)
6. Move selected spam to the ham list (you can also double click on the item)

## Implementation details

* Will automatically load the default classifier from `classifier.bin` on startup if available
* Will automatically save the current classifier to `classifier.bin` on exit
