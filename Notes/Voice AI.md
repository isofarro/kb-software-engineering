
Voice AI is more difficult that text-based chat interfaces:

* Text model is between a Transcriber and a Text-to-speech, that means additional latency
* Latency is more noticeable with audio than streamed text
* Personable AI assistants require high-quality voices
	* even high-quality voices can feel robotic
	* lower-quality voices the drop in human quality is noticeable to the point of off-putting.
* Every bit of noise that isn't transcribable is invisible to the model
	* Emotional tone or hostile volume is 
* Phone calls are a more hostile environment than the web


## Perceived performance

This is key for well-performing voice assistants that the performance is perceived to be responsive, even if it's not.

The main approach is when firing off the tool call to also have a start request message running asynchronously. The time taken to speak the "please hold" message runs in parallel to the API call, speech takes time, so the delay after the spoken message and the spoken result of API response is minimised to not feel slow or laggy.
