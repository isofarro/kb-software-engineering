
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

## No protocol for voice interfaces

A text interface guarantees when a conversation turn ends, it's hard-baked into the interface, despite it being unnatural. Conversations are turn based, like a text adventure game. You type something, and wait for the adventure to respond. It's clean, and clinical, and repeatable. And nothing like the real world.

With a voice, based on a text LLM where taking turns is baked into the foundation of the model API 