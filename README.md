# ![](res/karat.webp) karat

<p align=center>In-game spam filter for Dofus. Named after the Meridia of tranquility.</p>

<p align=center>Windows only.</p>

<p align=center><a href="https://donate.stripe.com/test_14k02tgZo1xG7WEcMM"><img src="https://github.com/Airtz/karat/blob/main/res/donate.png" width=110 height=132/></a></p>

## Getting started

1. Download karat binaries from the `bin` directory
2. Launch your Dofus client(s)
3. Load your character(s)
4. Launch karat.exe

## UI breakdown

<p align=center><img src="https://github.com/Airtz/karat/blob/main/res/collapsed_ui.png"/></p>

1. Load a classifier
2. Save the current classifier
3. Probability threshold above which messages are classified as spams
4. Mode
    * `Log`: log messages for manual training
    * `Filter`: log messages for manual training and filter spams
    * `Filter + Training`: log messages for manual training, filter spams and automatic training
6. Expand or collapse the UI

<p align=center><img src="https://github.com/Airtz/karat/blob/main/res/expanded_ui.png"/></p>

1. Spam list
    * `Channel`: channel in which the message was sent
    * `Sender`: name of the sender
    * `p`: probability of the message being a spam according to the classifier
3. Ham (non-spam) list
4. Train the classifier to classify listed spams and hams as such and then retrieve the current log
5. Move selected ham to the spam list (you can also double click on the item)
6. Move selected spam to the ham list (you can also double click on the item)

## Training the classifier

If the accuracy of the provided classifier is not good enough, you can train your own.

Expand the UI and manually classify messages as spams or hams using move buttons then hit the train and sync button. Repeat until the accuracy is good enough.

For obvious reasons it is not recommended to use the `Filter + Train` mode with low accuracy classifiers.

## Implementation details

* Will automatically load the default classifier `classifier.bin` on startup if available
* Will automatically save the current classifier to `classifier.bin` on exit
