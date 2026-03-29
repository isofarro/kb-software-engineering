Never make Voice AI the first AI-based product you do. Despite being built on top of text-based LLMs, the environment is fraught with difficulties and complications because of the audio layer. Particularly that the audio layer is built on top of a text LLM with text-based assumptions that simply don't hold at the audio level.

Voice AI is more difficult that text-based chat interfaces:

* Text model is between a Transcriber and a Text-to-speech, that means additional latency
* Latency is more noticeable with audio than streamed text
* Personable AI assistants require high-quality voices
	* even high-quality voices can feel robotic
	* lower-quality voices the drop in human quality is noticeable to the point of off-putting.
* Every bit of noise that isn't transcribable is invisible to the model
	* LLM models are deaf to emotional tone, hostile volume, frustration.
	* LLM models are oblivious to sarcasm or mockery
	* Background noise can prevent a transcriber from recording the actual words spoken
	* LLM models are deaf to speech disfluencies (ummm), and half-words.
	* LLMs are unused to barge-in and interrupting respondents
* Phone calls are a more hostile environment than the web
* Lack of physical or deterministic guard rails on Voice AI platforms
	* stems from the lack of maturity or keeping up with best practices
	* can't catch untoward/dangerous model output
	* webhook listeners can operate in parallel, but it's trying to claw back bad things after they've been vocalised by the text-to-speech
* Difficult tradeoffs: performance versus security
* All data in a Voice AI prompt will leak, given time and persistence. prompt drift effectively guarantees that

## Good VoiceAI is about empathy and design experience

"What we need is a Voice AI designer"

Voice AI is a technical challenge, as well as a human interface design challenge. They interlink, because a good quality conversation is affected by technical tradeoffs. And yet, solving the technical aspect doesn't guarantee a fluid human interaction.

## Perceived performance

This is key for well-performing voice assistants that the performance is perceived to be responsive, even if it's not.

The main approach is when firing off the tool call to also have a start request message running asynchronously. The time taken to speak the "please hold" message runs in parallel to the API call, speech takes time, so the delay after the spoken message and the spoken result of API response is minimised to not feel slow or laggy.

## Voice AI is more hostile than the Web

Douglas Crockford made the point that the Web is the most hostile programming environment, because it does not guarantee that code meant to run, is actually retrieved, interpreted or run. Or safe.

## Voice interfaces aren't turn-based

A text interface guarantees when a conversation turn ends, it's hard-baked into the interface, despite it being unnatural. Conversations are turn based, like a text adventure game. You type something, and wait for the adventure to respond. It's clean, and clinical, and repeatable. And nothing like the real world.

With a voice, based on a text LLM where taking turns is baked into the foundation of the model API (an array of messages), this is brittle. Like using long-polling in the early web to simulate a live connection (before we had web-sockets)

It requires a degree of politeness from a call respondent for a good call experience. Meaning they know they are talking to something that's not quite a fully adult human. An actual human adapts and recognises audio cues that the LLM cannot experience. A Voice AI requires a spoken "yes", a human can deal with an "uh-huh"

So, paradoxically, the illusion has to be broken, for the illusion of a voice conversation to work.

Humans don't expect to be called by voice AI assistants. It can be convincing, and feel human, up until the illusion breaks down because something that is completely natural in a human to human conversation fails at an audio assistant level. Particularly in cultures where wordplay, self-deprecation, irony and sarcasm is typical.

## Voice has emotional context

Voice calls are an artificial degradation of face-to-face conversation. We lose the visual cues available in face-to-face conversation. We adapt by tuning in on vocal and audio cues, beyond just the words spoken.

A voice AI platform that's using a transcriber (standalone or within the LLM model). That loses the audio cues and emotional inflections. Also interruptions are not naturally handled, since a text-based model has no concept of when so

## The folly of speech-native models

Although the idea of an LLM that natively supports audio is compelling (e.g. `gpt-realtime`, there are issues with turning that into a compelling Voice AI solution:

* Less choice/flexibility/tuning of transcribers. You don't get to use the best-of-breed transcribers.
* The output voices available are robotic, and well below the current quality of 11labs and Cartesia voices. They'll be obviously bot calls, robotic in tone despite being more fluid on the language level.
	* Sure, you can use these higher quality voices instead of the built-in `gpt-realtime` voices, but you're still paying the higher cost on output regardless of whether it's text or audio.
	* What are you gaining by using an **audio-in/audio-out** model?
* The cost of realtime models is currently 8 times the price for input, and 4 times the price for output than of the comparable text model.
* With the more rigid structure, there's less choice of languages. When public facing, having English-only is limiting when a chunk of your intended audience has other languages as a primary language, or even various local dialects of English.
	* Much like the voice-activated lift in Scotland, spoken dialect English is a more difficult proposition than a written English with dialect phrasings.