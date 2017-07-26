# Save text to audio file programmatically

up vote 4 down vote favorite

****

It's possible to save text as audio file as shown in screenshot. Now my question is that how to do the same programmatically. ![enter image description here](http://i.stack.imgur.com/Vvs1H.png)

Any help greatly appreciated. 

[objective-c](/questions/tagged/objective-c) [osx](/questions/tagged/osx)

[share](/q/29690847)|[improve this question](/posts/29690847/edit)

asked Apr 17 '15 at 5:11

![](https://i.stack.imgur.com/0zNBn.png?s=32&g=1)

[iDev](/users/1554347/idev)

2,814101936

add a comment | 

##  2 Answers 2

[ active](/questions/29690847/save-text-to-audio-file-programmatically?answertab=active#tab-top) [ oldest](/questions/29690847/save-text-to-audio-file-programmatically?answertab=oldest#tab-top) [ votes](/questions/29690847/save-text-to-audio-file-programmatically?answertab=votes#tab-top)

up vote 3 down vote accepted

`NSSpeechSynthesizer` does that job.

Say we have the property :

    
    
    @property  NSSpeechSynthesizer *synth;
    

that we initialize like this:

    
    
    synth = [[NSSpeechSynthesizer alloc] initWithVoice:nil];
    

we can do:

    
    
    NSURL *saveURL = [NSURL fileURLWithPath:[@"~/Desktop/SpokenText.aiff" stringByExpandingTildeInPath]];
    [synth startSpeakingString:@"A spoken short text" toURL:saveURL];
    

Before saving, we probably want to change the voice or the volume:

    
    
    [synth setVolume:0.5f];
    [synth setVoice:voiceID];
    

where the `value for volume` is expressed in floating-point units ranging from 0.0 through 1.0 and `voiceID` is a `voice identifier`. 

  
  
  
To see all available voice identifiers:

    
    
    NSArray *voiceIdentifiers = [NSSpeechSynthesizer availableVoices];
    NSLog(@"%li %@",voiceIdentifiers.count,voiceIdentifiers);
    

Output on `OS X 10.10.3` with all voices installed:

    
    
    101 (
        "com.apple.speech.synthesis.voice.Agnes",
        "com.apple.speech.synthesis.voice.Albert",
        "com.apple.speech.synthesis.voice.Alex",
        "com.apple.speech.synthesis.voice.alice.premium",
        "com.apple.speech.synthesis.voice.allison.premium",
        "com.apple.speech.synthesis.voice.alva.premium",
        "com.apple.speech.synthesis.voice.amelie.premium",
        "com.apple.speech.synthesis.voice.angelica.premium",
        "com.apple.speech.synthesis.voice.anna.premium",
        "com.apple.speech.synthesis.voice.audrey.premium",
        "com.apple.speech.synthesis.voice.aurelie.premium",
        "com.apple.speech.synthesis.voice.ava.premium",
        "com.apple.speech.synthesis.voice.BadNews",
        "com.apple.speech.synthesis.voice.Bahh",
        "com.apple.speech.synthesis.voice.Bells",
        "com.apple.speech.synthesis.voice.Boing",
        "com.apple.speech.synthesis.voice.Bruce",
        "com.apple.speech.synthesis.voice.Bubbles",
        "com.apple.speech.synthesis.voice.carlos.premium",
        "com.apple.speech.synthesis.voice.carmit.premium",
        "com.apple.speech.synthesis.voice.catarina.premium",
        "com.apple.speech.synthesis.voice.Cellos",
        "com.apple.speech.synthesis.voice.cem.premium",
        "com.apple.speech.synthesis.voice.chantal.premium",
        "com.apple.speech.synthesis.voice.claire.premium",
        "com.apple.speech.synthesis.voice.damayanti.premium",
        "com.apple.speech.synthesis.voice.daniel.premium",
        "com.apple.speech.synthesis.voice.Deranged",
        "com.apple.speech.synthesis.voice.diego.premium",
        "com.apple.speech.synthesis.voice.ellen.premium",
        "com.apple.speech.synthesis.voice.ewa.premium",
        "com.apple.speech.synthesis.voice.federica.premium",
        "com.apple.speech.synthesis.voice.felipe.premium",
        "com.apple.speech.synthesis.voice.fiona.premium",
        "com.apple.speech.synthesis.voice.Fred",
        "com.apple.speech.synthesis.voice.GoodNews",
        "com.apple.speech.synthesis.voice.henrik.premium",
        "com.apple.speech.synthesis.voice.Hysterical",
        "com.apple.speech.synthesis.voice.ioana.premium",
        "com.apple.speech.synthesis.voice.iveta.premium",
        "com.apple.speech.synthesis.voice.joana.premium",
        "com.apple.speech.synthesis.voice.jorge.premium",
        "com.apple.speech.synthesis.voice.juan.premium",
        "com.apple.speech.synthesis.voice.Junior",
        "com.apple.speech.synthesis.voice.kanya.premium",
        "com.apple.speech.synthesis.voice.karen.premium",
        "com.apple.speech.synthesis.voice.kate.premium",
        "com.apple.speech.synthesis.voice.Kathy",
        "com.apple.speech.synthesis.voice.katya.premium",
        "com.apple.speech.synthesis.voice.klara.premium",
        "com.apple.speech.synthesis.voice.kyoko.premium",
        "com.apple.speech.synthesis.voice.laura.premium",
        "com.apple.speech.synthesis.voice.lee.premium",
        "com.apple.speech.synthesis.voice.lekha.premium",
        "com.apple.speech.synthesis.voice.luca.premium",
        "com.apple.speech.synthesis.voice.luciana.premium",
        "com.apple.speech.synthesis.voice.magnus.premium",
        "com.apple.speech.synthesis.voice.mariska.premium",
        "com.apple.speech.synthesis.voice.markus.premium",
        "com.apple.speech.synthesis.voice.mei-jia.premium",
        "com.apple.speech.synthesis.voice.melina.premium",
        "com.apple.speech.synthesis.voice.milena.premium",
        "com.apple.speech.synthesis.voice.moira.premium",
        "com.apple.speech.synthesis.voice.monica.premium",
        "com.apple.speech.synthesis.voice.nicolas.premium",
        "com.apple.speech.synthesis.voice.nikos.premium",
        "com.apple.speech.synthesis.voice.nora.premium",
        "com.apple.speech.synthesis.voice.oliver.premium",
        "com.apple.speech.synthesis.voice.oskar.premium",
        "com.apple.speech.synthesis.voice.otoya.premium",
        "com.apple.speech.synthesis.voice.paola.premium",
        "com.apple.speech.synthesis.voice.paulina.premium",
        "com.apple.speech.synthesis.voice.petra.premium",
        "com.apple.speech.synthesis.voice.Organ",
        "com.apple.speech.synthesis.voice.Princess",
        "com.apple.speech.synthesis.voice.Ralph",
        "com.apple.speech.synthesis.voice.samantha.premium",
        "com.apple.speech.synthesis.voice.sara.premium",
        "com.apple.speech.synthesis.voice.satu.premium",
        "com.apple.speech.synthesis.voice.serena.premium",
        "com.apple.speech.synthesis.voice.sin-ji.premium",
        "com.apple.speech.synthesis.voice.soledad.premium",
        "com.apple.speech.synthesis.voice.susan.premium",
        "com.apple.speech.synthesis.voice.tarik.premium",
        "com.apple.speech.synthesis.voice.tessa.premium",
        "com.apple.speech.synthesis.voice.thomas.premium",
        "com.apple.speech.synthesis.voice.ting-ting.premium",
        "com.apple.speech.synthesis.voice.tom.premium",
        "com.apple.speech.synthesis.voice.Trinoids",
        "com.apple.speech.synthesis.voice.veena.premium",
        "com.apple.speech.synthesis.voice.Vicki",
        "com.apple.speech.synthesis.voice.Victoria",
        "com.apple.speech.synthesis.voice.Whisper",
        "com.apple.speech.synthesis.voice.xander.premium",
        "com.apple.speech.synthesis.voice.yannick.premium",
        "com.apple.speech.synthesis.voice.yelda.premium",
        "com.apple.speech.synthesis.voice.yuna.premium",
        "com.apple.speech.synthesis.voice.yuri.premium",
        "com.apple.speech.synthesis.voice.Zarvox",
        "com.apple.speech.synthesis.voice.zosia.premium",
        "com.apple.speech.synthesis.voice.zuzana.premium"
    )
    

[share](/a/29691135)|[improve this answer](/posts/29691135/edit)

[edited Apr 17 '15 at 6:25](/posts/29691135/revisions)

answered Apr 17 '15 at 5:32

user3577225 

  
 

Have tried it bool b = [synthesizer startSpeakingString:@"I have started speaking" toURL:[NSURL URLWithString:@"/Desktop"]]; returns true but can't find the file - [iDev](/users/1554347/idev) Apr 17 '15 at 5:48

1

 

solved with initFileURLWithPath :) Tnx @Zero - [iDev](/users/1554347/idev) Apr 17 '15 at 6:05

  
 

Cool, thanks. I added the URL-creation also to the code so the answer is clearer. - user3577225 Apr 17 '15 at 6:07

  
 

Great! and is there any solution for iOS for the same case? - [iDev](/users/1554347/idev) Apr 17 '15 at 6:08

add a comment | 

up vote 0 down vote

Starting from iOS 7 Apple provides the following API...

<https://developer.apple.com/library/ios/documentation/AVFoundation/Reference/AVSpeechSynthesizer_Ref/Reference/Reference.html>

See this answer <http://stackoverflow.com/a/17465494/215748>

    
    
    #import <AVFoundation/AVFoundation.h>
    …
    AVSpeechUtterance *utterance = [AVSpeechUtterance 
                                speechUtteranceWithString:@"Hello world"];
    AVSpeechSynthesizer *synth = [[AVSpeechSynthesizer alloc] init];
    [synth speakUtterance:utterance];
    

[share](/a/29690964)|[improve this answer](/posts/29690964/edit)

answered Apr 17 '15 at 5:20

![](https://www.gravatar.com/avatar/729fe0ee6cf13e7d7a99191fe9ecf194?s=32&d=identicon&r=PG&f=1)

[Rahul](/users/4743213/rahul)

674110

  
 

My question is to save as audio file instead of speak via speaker. Rather I need mac support. - [iDev](/users/1554347/idev) Apr 17 '15 at 5:28

  
 

Yeah, convert Text to audio and then record this audio.... - [Rahul](/users/4743213/rahul) Apr 17 '15 at 5:32

  
 

See this url : [appcoda.com/text-to-speech-ios-tutorial](http://www.appcoda.com/text-to-speech-ios-tutorial/) - [Rahul](/users/4743213/rahul) Apr 17 '15 at 5:34

  
 

recording an audio is not a great idea - [iDev](/users/1554347/idev) Apr 17 '15 at 5:38

  
 

Text to audio convert then file save... - [Rahul](/users/4743213/rahul) Apr 17 '15 at 5:40

 |  show **2** more comments

