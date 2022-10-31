# ![](res/karat.webp) karat

<p align=center>In-game spam filter for Dofus. Named after the Meridia of tranquility.</p>

<p align=center>Windows only.</p>

<p align=center><a href="https://donate.stripe.com/7sI6rK74C7Wk2C46oo"><img src="https://github.com/Airtz/karat/blob/main/res/support.png" width=110 height=132/></a></p>

## Getting started

1. [Download](https://github.com/Airtz/karat/releases) the latest release
2. Launch your Dofus client(s)
3. Load your character(s)
4. Launch `karat.exe`

## In-game commands

<p align=center><img src="https://github.com/Airtz/karat/blob/main/res/help.png"/></p>

Input must be prefixed with `$`. Make sure to enable your `informations` channel. Availables commands are:

* `help` - show this message
* `load` [path] - load a classifier from the default path or a specified one
* `save` [path] - save the current classifier to the default path or a specified one
* `mode` &lt;log|filter|learn&gt; - set the operating mode
* `train` - open the training UI
* `amplitude` &lt;value&gt; - set the current classifier amplitude

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

## Amplitude

Filtering is done using a Multinomial Naive Bayes Classifier. Likelihood ratios are clamped between amplitude `a` and `1/a`.

Default value for `a` is 100.

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
