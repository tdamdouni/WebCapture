# Changing Voices in Swift for iOS

_Captured: 2016-04-22 at 21:00 from [www.ikiapps.com](http://www.ikiapps.com/tips/2015/12/30/setting-voice-for-tts-in-ios.html)_

When your phone speaks to you, what voice is it using?

The quality of digital voices has improved to the point where using text-to-speech (TTS) can provide significant benefits within many contexts.

I'm excited to use TTS in my apps and iOS offers a number of quality voices by default. Getting iOS to talk only requires a few simple steps.

To give you an idea of the voices that are available, I've extracted the array of available voices from an iPhone running iOS 9.2.
    
    
    [AVSpeechSynthesisVoice 0x17e30940] Language: ar-SA, Name: Maged, Quality: Default, 
    [AVSpeechSynthesisVoice 0x17d3e150] Language: cs-CZ, Name: Zuzana, Quality: Default, 
    [AVSpeechSynthesisVoice 0x17e79700] Language: da-DK, Name: Sara, Quality: Default, 
    [AVSpeechSynthesisVoice 0x17e50c50] Language: de-DE, Name: Anna, Quality: Default, 
    [AVSpeechSynthesisVoice 0x17ec30f0] Language: el-GR, Name: Melina, Quality: Default, 
    [AVSpeechSynthesisVoice 0x17e687f0] Language: en-AU, Name: Karen, Quality: Default, 
    [AVSpeechSynthesisVoice 0x17e23be0] Language: en-GB, Name: Daniel, Quality: Default, 
    [AVSpeechSynthesisVoice 0x17e6ffc0] Language: en-IE, Name: Moira, Quality: Default, 
    [AVSpeechSynthesisVoice 0x17ec79b0] Language: en-US, Name: Samantha (Enhanced), Quality: Enhanced, 
    [AVSpeechSynthesisVoice 0x17e795a0] Language: en-US, Name: Samantha, Quality: Default, 
    [AVSpeechSynthesisVoice 0x17e75900] Language: en-ZA, Name: Tessa, Quality: Default, 
    [AVSpeechSynthesisVoice 0x17e27ec0] Language: es-ES, Name: Monica, Quality: Default, 
    [AVSpeechSynthesisVoice 0x17ec5e10] Language: es-MX, Name: Paulina, Quality: Default, 
    [AVSpeechSynthesisVoice 0x17e799c0] Language: fi-FI, Name: Satu, Quality: Default, 
    [AVSpeechSynthesisVoice 0x17ec61c0] Language: fr-CA, Name: Amelie, Quality: Default, 
    [AVSpeechSynthesisVoice 0x17e75b10] Language: fr-FR, Name: Thomas, Quality: Default, 
    [AVSpeechSynthesisVoice 0x17ee2460] Language: he-IL, Name: Carmit, Quality: Default, 
    [AVSpeechSynthesisVoice 0x17ef5140] Language: hi-IN, Name: Lekha, Quality: Default, 
    [AVSpeechSynthesisVoice 0x17e6f840] Language: hu-HU, Name: Mariska, Quality: Default, 
    [AVSpeechSynthesisVoice 0x17e59bd0] Language: id-ID, Name: Damayanti, Quality: Default, 
    [AVSpeechSynthesisVoice 0x17d2c950] Language: it-IT, Name: Alice, Quality: Default, 
    [AVSpeechSynthesisVoice 0x17ebaec0] Language: ja-JP, Name: Kyoko, Quality: Default, 
    [AVSpeechSynthesisVoice 0x17d42100] Language: ko-KR, Name: Yuna, Quality: Default, 
    [AVSpeechSynthesisVoice 0x17ee3130] Language: nl-BE, Name: Ellen, Quality: Default, 
    [AVSpeechSynthesisVoice 0x17d637d0] Language: nl-NL, Name: Xander, Quality: Default, 
    [AVSpeechSynthesisVoice 0x17e7c8b0] Language: no-NO, Name: Nora, Quality: Default, 
    [AVSpeechSynthesisVoice 0x17d3e430] Language: pl-PL, Name: Zosia, Quality: Default, 
    [AVSpeechSynthesisVoice 0x17e33190] Language: pt-BR, Name: Luciana, Quality: Default, 
    [AVSpeechSynthesisVoice 0x17eabf00] Language: pt-PT, Name: Joana, Quality: Default, 
    [AVSpeechSynthesisVoice 0x17e2a650] Language: ro-RO, Name: Ioana, Quality: Default, 
    [AVSpeechSynthesisVoice 0x17e232b0] Language: ru-RU, Name: Milena, Quality: Default, 
    [AVSpeechSynthesisVoice 0x17ee6830] Language: sk-SK, Name: Laura, Quality: Default, 
    [AVSpeechSynthesisVoice 0x17e64a10] Language: sv-SE, Name: Alva, Quality: Default, 
    [AVSpeechSynthesisVoice 0x17e62fc0] Language: th-TH, Name: Kanya, Quality: Default, 
    [AVSpeechSynthesisVoice 0x17df4080] Language: tr-TR, Name: Yelda, Quality: Default, 
    [AVSpeechSynthesisVoice 0x17e76a10] Language: zh-CN, Name: Ting-Ting (Enhanced), Quality: Enhanced, 
    [AVSpeechSynthesisVoice 0x17db4850] Language: zh-CN, Name: Ting-Ting, Quality: Default, 
    [AVSpeechSynthesisVoice 0x17e2ecf0] Language: zh-HK, Name: Sin-Ji, Quality: Default, 
    [AVSpeechSynthesisVoice 0x17e224c0] Language: zh-TW, Name: Mei-Jia, Quality: Default]

iOS has a nice method for setting the voice but there is only support for a single identifier, the Alex voice.
    
    
    let voice = AVSpeechSynthesisVoice(identifier: AVSpeechSynthesisVoiceIdentifierAlex)

**To use another voice, the array of voices can be searched for a matching name.** The `identifier` in the previous call does not match the name of a voice as you might imagine it to.
    
    
    var voiceToUse: AVSpeechSynthesisVoice?
    for voice in AVSpeechSynthesisVoice.speechVoices() {
        if #available(iOS 9.0, *) {
            if voice.name == "Karen" {
            voiceToUse = voice
            }
        } 
    } 

To use voice, assign the voice using the `voice` property on an utterance and then speak the utterance.
    
    
    let utterance = AVSpeechUtterance(string: "Hello from iOS.")
    utterance.voice = voiceToUse
    let synth = AVSpeechSynthesizer()
    synth.speakUtterance(utterance)
