# AI-901 Practice Exam: Azure Speech in Foundry Tools

**Focus:** Speech-to-Text (Speech Recognition) and Text-to-Speech (Speech Synthesis)
**Questions:** 55 | **Time:** ~60 minutes | **Difficulty:** Progressive (Easy -> Hard)

---

## Section A: Foundations (Questions 1-10)

**Q1.** What Python package must you install to use Azure Speech in Foundry Tools?

A) `pip install azure-speech`
B) `pip install azure-cognitiveservices-speech`
C) `pip install azure-ai-speech`
D) `pip install azure-foundry-speech`

---

**Q2.** Which import statement is correct for Azure Speech SDK?

A) `import azure.speech as speechsdk`
B) `from azure.cognitiveservices import speech`
C) `import azure.cognitiveservices.speech as speechsdk`
D) `from azure.ai.speech import SpeechClient`

---

**Q3.** True or False: `SpeechRecognizer` is the class used for Text-to-Speech.

A) True
B) False

---

**Q4.** What two parameters does `SpeechConfig` require?

A) `api_key` and `region`
B) `subscription` and `endpoint`
C) `key` and `url`
D) `credentials` and `host`

---

**Q5.** Match each class to its role:

| Class | Role |
|-------|------|
| 1. SpeechConfig | A. Converts text to spoken audio |
| 2. AudioConfig | B. Holds subscription key and endpoint |
| 3. SpeechRecognizer | C. Defines audio input source |
| 4. SpeechSynthesizer | D. Converts spoken audio to text |

A) 1-B, 2-C, 3-D, 4-A
B) 1-C, 2-B, 3-A, 4-D
C) 1-B, 2-A, 3-C, 4-D
D) 1-A, 2-C, 3-D, 4-B

---

**Q6.** Which class is used to configure where synthesized audio is sent (e.g., speaker or file)?

A) `AudioConfig`
B) `AudioOutputConfig`
C) `SpeechOutputConfig`
D) `OutputAudioConfig`

---

**Q7.** True or False: `AudioConfig` is used to specify the input source for speech recognition (e.g., microphone or audio file).

A) True
B) False

---

**Q8.** What is the correct way to create an audio config for the default microphone?

A) `speechsdk.audio.AudioConfig(microphone=True)`
B) `speechsdk.audio.AudioConfig(use_default_microphone=True)`
C) `speechsdk.audio.AudioConfig(input="microphone")`
D) `speechsdk.audio.AudioConfig.from_microphone()`

---

**Q9.** In the Azure Speech pipeline, what does the acoustic model do?

A) Maps phonemes to words
B) Converts audio signals to phonemes
C) Generates audio from text
D) Selects the appropriate voice

---

**Q10.** In the Azure Speech pipeline, what does the language model do?

A) Converts audio signals to phonemes
B) Translates text between languages
C) Maps phonemes to words
D) Generates synthetic speech

---

### Answers: Section A (Questions 1-10)

| Q | Answer | Explanation |
|---|--------|-------------|
| 1 | **B** | The correct package is `azure-cognitiveservices-speech`. Other options are fabricated package names. |
| 2 | **C** | The SDK is imported as `import azure.cognitiveservices.speech as speechsdk`. This is the standard convention used throughout the documentation. |
| 3 | **B (False)** | `SpeechRecognizer` is for Speech-to-Text (recognition). `SpeechSynthesizer` is for Text-to-Speech (synthesis). |
| 4 | **B** | `SpeechConfig(subscription=speech_key, endpoint=endpoint_url)` takes a subscription key and an endpoint URL. |
| 5 | **A** | SpeechConfig holds config (B), AudioConfig defines input source (C), SpeechRecognizer does STT (D), SpeechSynthesizer does TTS (A). |
| 6 | **B** | `speechsdk.audio.AudioOutputConfig` configures the output destination for synthesized speech (speaker or file). `AudioConfig` is for input. |
| 7 | **A (True)** | `AudioConfig` specifies input sources like `use_default_microphone=True` or a file path for speech recognition. |
| 8 | **B** | The correct parameter is `use_default_microphone=True` in the `AudioConfig` constructor. |
| 9 | **B** | The acoustic model converts raw audio signals into phonemes (basic units of sound). |
| 10 | **C** | The language model takes phonemes produced by the acoustic model and maps them to words and sentences. |

---

## Section B: Speech-to-Text Deep Dive (Questions 11-20)

**Q11.** What event fires when the Speech service has fully recognized a spoken phrase?

A) `recognizing`
B) `recognized`
C) `completed`
D) `transcribed`

---

**Q12.** What event fires for partial/interim transcription results while the user is still speaking?

A) `recognized`
B) `partial`
C) `recognizing`
D) `streaming`

---

**Q13.** A developer writes this code but sees no output. What is wrong?

```python
speech_config = speechsdk.SpeechConfig(subscription=key, endpoint=url)
audio_config = speechsdk.audio.AudioConfig(use_default_microphone=True)
speech_recognizer = speechsdk.SpeechRecognizer(speech_config=speech_config, audio_config=audio_config)

def handler(evt):
    print(evt.result.text)

speech_recognizer.recognized.connect(handler)
speech_recognizer.start_continuous_recognition()
```

A) The handler function signature is wrong
B) The program likely exits immediately after `start_continuous_recognition()` -- it needs something to keep it running (e.g., a wait or loop)
C) `recognized` is not a valid event name
D) `audio_config` should use `AudioOutputConfig`

---

**Q14.** Which method starts continuous speech recognition that keeps listening?

A) `speech_recognizer.recognize()`
B) `speech_recognizer.start_continuous_recognition()`
C) `speech_recognizer.listen()`
D) `speech_recognizer.begin_recognition()`

---

**Q15.** Which method stops continuous recognition?

A) `speech_recognizer.end()`
B) `speech_recognizer.cancel()`
C) `speech_recognizer.stop_continuous_recognition()`
D) `speech_recognizer.close()`

---

**Q16.** Fill in the blank to connect the handler to final recognition results:

```python
speech_recognizer._______.connect(my_handler)
```

A) `on_recognized`
B) `recognized`
C) `result`
D) `final_result`

---

**Q17.** A company needs to transcribe 10,000 stored audio files overnight. Which approach is best?

A) Real-time transcription using `SpeechRecognizer` for each file
B) Batch transcription
C) Continuous recognition on a loop
D) Text-to-Speech with reverse processing

---

**Q18.** True or False: Batch transcription processes stored audio files asynchronously with best-effort scheduling.

A) True
B) False

---

**Q19.** What is the key difference between real-time transcription and batch transcription?

A) Real-time is more accurate
B) Real-time processes live audio streams; batch processes stored audio files asynchronously
C) Batch transcription only works with WAV files
D) Real-time transcription requires a GPU

---

**Q20.** A developer writes the following. What does `evt.result.text` contain inside the `recognizing_handler`?

```python
def recognizing_handler(evt):
    print(f"Recognizing: {evt.result.text}")

speech_recognizer.recognizing.connect(recognizing_handler)
```

A) The final, committed transcription
B) A partial/interim transcription that may change as more audio is processed
C) An error message
D) The name of the audio source

---

### Answers: Section B (Questions 11-20)

| Q | Answer | Explanation |
|---|--------|-------------|
| 11 | **B** | The `recognized` event fires when the service has finalized recognition of a phrase. |
| 12 | **C** | The `recognizing` event provides partial/interim results while audio is still being processed. |
| 13 | **B** | `start_continuous_recognition()` is non-blocking. The program exits immediately unless something (like `time.sleep()`, an event wait, or input loop) keeps the main thread alive. |
| 14 | **B** | `start_continuous_recognition()` begins ongoing listening that persists until explicitly stopped. |
| 15 | **C** | `stop_continuous_recognition()` gracefully ends the continuous recognition session. |
| 16 | **B** | The event property is `recognized` -- you call `speech_recognizer.recognized.connect(handler)`. |
| 17 | **B** | Batch transcription is designed for processing large volumes of stored audio files asynchronously with best-effort scheduling. |
| 18 | **A (True)** | Batch transcription is asynchronous and uses best-effort scheduling, making it ideal for large-scale offline processing. |
| 19 | **B** | Real-time processes live audio streams (microphone, streaming input). Batch is designed for stored audio files and runs asynchronously. |
| 20 | **B** | The `recognizing` event provides interim/partial results. The text may change as the service continues to process audio and refine its prediction. |

---

## Section C: Text-to-Speech Deep Dive (Questions 21-30)

**Q21.** Which property sets the voice for speech synthesis?

A) `speech_config.voice = 'en-US-Ava'`
B) `speech_config.speech_synthesis_voice_name = 'en-US-Ava:DragonHDLatestNeural'`
C) `speech_config.set_voice('en-US-Ava')`
D) `speech_config.tts_voice = 'en-US-Ava:DragonHDLatestNeural'`

---

**Q22.** What does `speak_text_async(text).get()` do?

A) Starts synthesis in the background and never returns
B) Starts async synthesis and `.get()` blocks until the result is available
C) Sends text to be stored for later synthesis
D) Translates text to another language then speaks it

---

**Q23.** What value of `result.reason` indicates TTS completed successfully?

A) `speechsdk.ResultReason.Success`
B) `speechsdk.ResultReason.SynthesizingAudioCompleted`
C) `speechsdk.ResultReason.AudioReady`
D) `speechsdk.ResultReason.Completed`

---

**Q24.** What value of `result.reason` indicates TTS was canceled?

A) `speechsdk.ResultReason.Failed`
B) `speechsdk.ResultReason.Error`
C) `speechsdk.ResultReason.Canceled`
D) `speechsdk.ResultReason.Stopped`

---

**Q25.** When TTS is canceled due to an error, how do you access the error details?

A) `result.error_message`
B) `result.cancellation_details.error_details`
C) `result.reason.error`
D) `result.get_error()`

---

**Q26.** Fill in the blanks to complete this TTS code:

```python
speech_config = speechsdk.SpeechConfig(subscription=key, endpoint=url)
audio_config = speechsdk.audio._______(use_default_speaker=True)
speech_config._______ = 'en-US-Ava:DragonHDLatestNeural'
synthesizer = speechsdk._______(speech_config=speech_config, audio_config=audio_config)
```

A) `AudioConfig`, `voice_name`, `SpeechRecognizer`
B) `AudioOutputConfig`, `speech_synthesis_voice_name`, `SpeechSynthesizer`
C) `OutputConfig`, `synthesis_voice`, `TextToSpeech`
D) `AudioOutputConfig`, `voice`, `SpeechSynthesizer`

---

**Q27.** In TTS, what is the correct order of prosodic units from largest to smallest?

A) Phonemes -> Words -> Phrases -> Sentences
B) Sentences -> Clauses -> Phrases -> Phonemes
C) Phrases -> Sentences -> Clauses -> Phonemes
D) Words -> Phonemes -> Phrases -> Sentences

---

**Q28.** A developer's TTS code runs without errors but produces no audio. The code is:

```python
speech_config = speechsdk.SpeechConfig(subscription=key, endpoint=url)
speech_config.speech_synthesis_voice_name = 'en-US-Ava:DragonHDLatestNeural'
synthesizer = speechsdk.SpeechSynthesizer(speech_config=speech_config)
result = synthesizer.speak_text_async("Hello").get()
```

What is the most likely issue?

A) The voice name is invalid
B) No `AudioOutputConfig` was provided to direct audio to the speaker
C) `speak_text_async` should be `speak_text`
D) The `SpeechConfig` is missing the region parameter

---

**Q29.** What does the `:DragonHDLatestNeural` suffix indicate in the voice name `en-US-Ava:DragonHDLatestNeural`?

A) The voice uses a legacy non-neural engine
B) The voice uses a specific high-definition neural voice model variant
C) The voice is for dragon-themed content only
D) The voice requires a premium subscription tier

---

**Q30.** Which of the following are valid reasons for a TTS cancellation? (Select TWO)

A) `CancellationReason.Error` -- an error occurred (e.g., invalid key)
B) `CancellationReason.Timeout` -- the request timed out
C) `CancellationReason.EndOfStream` -- end of input
D) `CancellationReason.NetworkFailure` -- network issue

---

### Answers: Section C (Questions 21-30)

| Q | Answer | Explanation |
|---|--------|-------------|
| 21 | **B** | The property is `speech_synthesis_voice_name` on the `SpeechConfig` object. The full voice name includes locale, name, and model variant. |
| 22 | **B** | `speak_text_async()` starts synthesis asynchronously and returns a future. `.get()` blocks the calling thread until the result is ready. |
| 23 | **B** | `ResultReason.SynthesizingAudioCompleted` is the specific enum value indicating successful completion of speech synthesis. |
| 24 | **C** | `ResultReason.Canceled` indicates the synthesis operation was canceled, which could be due to an error or other reason. |
| 25 | **B** | You access the cancellation details via `result.cancellation_details`, then get the specific error from `.error_details`. |
| 26 | **B** | TTS output uses `AudioOutputConfig`, the voice property is `speech_synthesis_voice_name`, and the class is `SpeechSynthesizer`. |
| 27 | **B** | Prosodic units from largest to smallest: Sentences -> Clauses -> Phrases -> Phonemes. TTS breaks text into these units for natural-sounding speech. |
| 28 | **B** | Without an explicit `AudioOutputConfig(use_default_speaker=True)`, the synthesizer may not have a configured output destination. The audio config directs where the synthesized audio goes. |
| 29 | **B** | The suffix indicates a specific neural voice model variant. "DragonHDLatestNeural" refers to a high-definition neural voice engine version. |
| 30 | **A, C** | `CancellationReason.Error` covers errors like invalid keys or network issues. `CancellationReason.EndOfStream` indicates the end of the input stream. The other options are not standard SDK cancellation reasons. |

---

## Section D: Scenarios and Architecture (Questions 31-40)

**Q31.** A hospital wants to transcribe doctor-patient conversations in real time to populate medical records. Which components are needed? (Select ALL that apply)

A) `SpeechConfig` with subscription and endpoint
B) `AudioConfig` with microphone input
C) `SpeechRecognizer` with continuous recognition
D) `SpeechSynthesizer` for reading back the records
E) `recognized` event handler to capture final transcriptions

A) A, B, C, E only
B) A, B, C, D, E
C) A, C, E only
D) B, C, D only

---

**Q32.** You are building a voice assistant that listens to a user, transcribes their question, processes it, then speaks the answer back. Place these steps in the correct order:

1. Create `SpeechConfig`
2. Create `SpeechSynthesizer` with `AudioOutputConfig`
3. Create `SpeechRecognizer` with `AudioConfig` (microphone)
4. Call `start_continuous_recognition()`
5. Process the transcribed text in the `recognized` handler
6. Call `speak_text_async(answer).get()` to speak the response

A) 1 -> 3 -> 4 -> 5 -> 2 -> 6
B) 1 -> 2 -> 3 -> 4 -> 5 -> 6
C) 3 -> 1 -> 4 -> 5 -> 6 -> 2
D) 1 -> 4 -> 3 -> 5 -> 2 -> 6

---

**Q33.** A call center needs to transcribe 50,000 recorded phone calls stored as audio files. They need results by the next business day but do not need them instantly. What is the best approach?

A) Use real-time transcription with `SpeechRecognizer` in a loop
B) Use batch transcription for asynchronous processing of stored files
C) Use `SpeechSynthesizer` to convert the files
D) Use continuous recognition with `start_continuous_recognition()` on each file

---

**Q34.** What is "Voice Live" in the context of Azure Speech in Foundry Tools?

A) A feature for live-streaming audio to YouTube
B) Speech-capable agents that can engage in voice conversations
C) A voice cloning service
D) A real-time voice translation service

---

**Q35.** A developer is building an accessibility feature that reads web page content aloud. Which Azure Speech components are needed?

A) `SpeechRecognizer` + `AudioConfig`
B) `SpeechSynthesizer` + `AudioOutputConfig`
C) `SpeechRecognizer` + `AudioOutputConfig`
D) `SpeechSynthesizer` + `AudioConfig`

---

**Q36.** You need to build a system that both transcribes meeting audio AND generates spoken summaries at the end. Which combination of classes do you need?

A) Two `SpeechRecognizer` instances
B) `SpeechRecognizer` for transcription + `SpeechSynthesizer` for spoken summaries
C) Two `SpeechSynthesizer` instances
D) One `SpeechConfig` is sufficient for both tasks without additional classes

---

**Q37.** An IoT smart home device needs to listen for voice commands continuously. Which recognition method is most appropriate?

A) Single-shot recognition with `recognize_once()`
B) Continuous recognition with `start_continuous_recognition()`
C) Batch transcription
D) `speak_text_async()`

---

**Q38.** A developer wants to save synthesized speech to a file instead of playing it through speakers. What should they change?

A) Use `AudioConfig` instead of `AudioOutputConfig`
B) Use `AudioOutputConfig(filename="output.wav")` instead of `AudioOutputConfig(use_default_speaker=True)`
C) Set `speech_config.output_format = "file"`
D) Call `synthesizer.save_to_file("output.wav")`

---

**Q39.** Your application transcribes speech in English but users sometimes speak French. What part of the configuration would you modify to handle French input?

A) Change the `AudioConfig` to a French microphone
B) Set the recognition language on `SpeechConfig` (e.g., `speech_config.speech_recognition_language = "fr-FR"`)
C) Use a different `SpeechRecognizer` class for French
D) Change the `AudioOutputConfig` language setting

---

**Q40.** A kiosk application in an airport provides spoken directions in multiple languages. For TTS, what primarily needs to change for each language?

A) The `SpeechConfig` subscription key
B) The `speech_synthesis_voice_name` to a voice in the target language
C) The `AudioOutputConfig` speaker
D) The endpoint URL

---

### Answers: Section D (Questions 31-40)

| Q | Answer | Explanation |
|---|--------|-------------|
| 31 | **A** | Real-time transcription needs SpeechConfig (A), microphone input via AudioConfig (B), SpeechRecognizer for STT (C), and a recognized event handler (E). SpeechSynthesizer (D) is for TTS, not needed for transcription. |
| 32 | **A** | First create config (1), then the recognizer with mic input (3), start listening (4), process transcribed text (5), then create synthesizer (2) and speak the answer (6). The synthesizer can be created later since it is only needed for the response. |
| 33 | **B** | Batch transcription is designed for large volumes of stored audio files with asynchronous, best-effort scheduling -- perfect for overnight processing. |
| 34 | **B** | Voice Live refers to speech-capable agents that can conduct voice-based conversations with users. |
| 35 | **B** | Reading content aloud is Text-to-Speech, which requires `SpeechSynthesizer` and `AudioOutputConfig` (to direct audio to speakers). |
| 36 | **B** | Transcription requires `SpeechRecognizer` (STT) and generating spoken summaries requires `SpeechSynthesizer` (TTS). Both share the same `SpeechConfig`. |
| 37 | **B** | Continuous recognition with `start_continuous_recognition()` keeps listening indefinitely, ideal for always-on voice command detection. |
| 38 | **B** | `AudioOutputConfig(filename="output.wav")` directs synthesized audio to a file instead of the default speaker. |
| 39 | **B** | The recognition language is set on `SpeechConfig` using the `speech_recognition_language` property with the appropriate locale code. |
| 40 | **B** | For multi-language TTS, you change the `speech_synthesis_voice_name` to a voice in the desired language (e.g., `fr-FR-DeniseNeural` for French). |

---

## Section E: Error Handling and Edge Cases (Questions 41-50)

**Q41.** What happens if you provide an invalid subscription key to `SpeechConfig` and attempt recognition?

A) The recognizer silently returns empty results
B) A `recognized` event fires with an error in `evt.result.text`
C) The operation is canceled with `CancellationReason.Error` and error details indicating an authentication failure
D) Python raises an `ImportError`

---

**Q42.** Examine this error-handling code for TTS. What is missing?

```python
result = speech_synthesizer.speak_text_async(text).get()

if result.reason == speechsdk.ResultReason.SynthesizingAudioCompleted:
    print("Success")
elif result.reason == speechsdk.ResultReason.Canceled:
    print("Canceled")
```

A) Nothing -- the code is complete
B) It should check `result.cancellation_details.reason` for `CancellationReason.Error` and print `error_details`
C) It needs a `try/except` block around `speak_text_async`
D) It should check `result.audio_data` for None

---

**Q43.** What happens if `start_continuous_recognition()` is called but no microphone is connected?

A) The program waits silently forever
B) An error is raised or the session is canceled with an error indicating no audio input device
C) The recognizer uses the system speaker as input instead
D) It automatically switches to batch transcription mode

---

**Q44.** A developer passes an empty string to `speak_text_async("")`. What is the most likely outcome?

A) The synthesizer crashes with an unhandled exception
B) The synthesizer returns a result with `SynthesizingAudioCompleted` but produces no audible output (or very short silence)
C) The synthesizer raises a `ValueError`
D) The method call blocks indefinitely

---

**Q45.** What should you check FIRST when `result.reason` is `ResultReason.Canceled`?

A) The audio output device
B) `result.cancellation_details.reason` to determine if it was an error
C) The network speed
D) The voice name

---

**Q46.** A developer forgets to call `.get()` after `speak_text_async(text)`. What happens?

```python
result = speech_synthesizer.speak_text_async(text)
if result.reason == speechsdk.ResultReason.SynthesizingAudioCompleted:
    print("Done")
```

A) The code works fine
B) `result` is a future object, not the actual result -- accessing `.reason` will fail with an `AttributeError`
C) The audio plays but the condition never matches
D) The synthesis never starts

---

**Q47.** A `recognizing` event handler fires 15 times, then a `recognized` event fires once. What happened?

A) There were 15 errors followed by one success
B) The service provided 15 partial/interim transcriptions as audio was processed, then delivered the final transcription
C) 15 different sentences were partially recognized
D) The handler was connected incorrectly

---

**Q48.** You receive `CancellationReason.Error` with `error_details` stating "Connection was closed by the remote host." What is the most likely cause?

A) The voice name is misspelled
B) A network issue or service outage prevented the connection
C) The audio file format is unsupported
D) The subscription key has been rotated or expired

---

**Q49.** True or False: You can use both `recognized` and `recognizing` event handlers simultaneously on the same `SpeechRecognizer` instance.

A) True
B) False

---

**Q50.** A developer's continuous recognition stops working after a few minutes. The `recognized` events stop firing. What should they investigate FIRST?

A) Whether the microphone battery died or was disconnected
B) Whether `stop_continuous_recognition()` was accidentally called
C) Network connectivity and whether the session timed out or was interrupted
D) All of the above

---

### Answers: Section E (Questions 41-50)

| Q | Answer | Explanation |
|---|--------|-------------|
| 41 | **C** | An invalid key causes the operation to be canceled. You would see `ResultReason.Canceled` with `CancellationReason.Error` and error details about authentication failure. |
| 42 | **B** | The code catches cancellation but does not inspect why. Best practice is to check `cancellation_details.reason` for `CancellationReason.Error` and then print `cancellation_details.error_details` for debugging. |
| 43 | **B** | Without a microphone, the audio input cannot be established. The SDK will report an error through the cancellation mechanism indicating no audio input device is available. |
| 44 | **B** | An empty string is technically valid input. The synthesizer will likely return `SynthesizingAudioCompleted` but produce negligible or no audible audio. |
| 45 | **B** | Always check `cancellation_details.reason` first. If it is `CancellationReason.Error`, then examine `error_details` for the specific problem (bad key, network issue, etc.). |
| 46 | **B** | `speak_text_async()` returns a future (async result). Without `.get()`, `result` is the future object, not the synthesis result. Accessing `.reason` on the future raises an `AttributeError`. |
| 47 | **B** | The `recognizing` event fires repeatedly with partial results as the service processes audio in real time. Once the utterance is complete, `recognized` fires once with the final transcription. |
| 48 | **B** | "Connection closed by remote host" typically indicates a network issue, firewall blocking the connection, or a temporary service outage. However, an expired key (D) could also produce this. The connection error message points most directly to network/connectivity issues. |
| 49 | **A (True)** | You can (and often should) connect both event handlers to get both real-time partial results and final transcriptions from the same recognizer. |
| 50 | **D** | All of these are valid possibilities. Hardware issues (A), accidental stop calls (B), and network/session problems (C) can all cause recognition to stop. Investigate all of them systematically. |

---

## Section F: Advanced and Integration (Questions 51-55)

**Q51.** A developer writes the following code. How many objects related to the Speech SDK are created?

```python
import azure.cognitiveservices.speech as speechsdk

speech_config = speechsdk.SpeechConfig(subscription=key, endpoint=url)
audio_in = speechsdk.audio.AudioConfig(use_default_microphone=True)
audio_out = speechsdk.audio.AudioOutputConfig(use_default_speaker=True)
speech_config.speech_synthesis_voice_name = 'en-US-Ava:DragonHDLatestNeural'
recognizer = speechsdk.SpeechRecognizer(speech_config=speech_config, audio_config=audio_in)
synthesizer = speechsdk.SpeechSynthesizer(speech_config=speech_config, audio_config=audio_out)
```

A) 3 (config, recognizer, synthesizer)
B) 4 (config, audio_in, recognizer, synthesizer)
C) 5 (config, audio_in, audio_out, recognizer, synthesizer)
D) 6 (config, audio_in, audio_out, voice, recognizer, synthesizer)

---

**Q52.** A voice-enabled customer service bot needs to:
(i) Listen to the customer,
(ii) Transcribe what they say,
(iii) Send the text to an AI model for a response,
(iv) Speak the response back.

Which pair of Azure Speech classes handles steps (i)+(ii) and step (iv) respectively?

A) `SpeechSynthesizer` and `SpeechRecognizer`
B) `SpeechRecognizer` and `SpeechSynthesizer`
C) `AudioConfig` and `AudioOutputConfig`
D) `SpeechConfig` and `SpeechConfig`

---

**Q53.** What is the output of the following code if the subscription key is valid but the user says "Hello world"?

```python
def recognized_handler(evt):
    print(f"Final: {evt.result.text}")

def recognizing_handler(evt):
    print(f"Partial: {evt.result.text}")

speech_recognizer.recognized.connect(recognized_handler)
speech_recognizer.recognizing.connect(recognizing_handler)
speech_recognizer.start_continuous_recognition()
# (user says "Hello world" and then pauses)
```

A) Only `Final: Hello world.` is printed
B) One or more `Partial:` lines are printed (e.g., `Partial: Hello`, `Partial: Hello world`), followed by `Final: Hello world.`
C) Only `Partial: Hello world` is printed
D) Nothing is printed because there is no loop

---

**Q54.** You are reviewing code that uses `os.environ.get('FOUNDRY_KEY')` and `os.environ.get('ENDPOINT')` for the SpeechConfig. Why is this approach preferred over hardcoding the key?

A) It is faster at runtime
B) It keeps secrets out of source code, improving security
C) Environment variables are encrypted automatically
D) The SDK requires environment variables and does not accept string literals

---

**Q55.** A team is building a multilingual voice application. They need STT in Spanish, processing in English, and TTS response in Japanese. Which configuration items change for each stage?

A) Only the `SpeechConfig` subscription key changes
B) STT: set `speech_recognition_language` to `es-ES`; Processing: application logic (no SDK change); TTS: set `speech_synthesis_voice_name` to a Japanese voice
C) A separate Azure subscription is needed for each language
D) Only the `AudioConfig` changes for each language

---

### Answers: Section F (Questions 51-55)

| Q | Answer | Explanation |
|---|--------|-------------|
| 51 | **C** | Five SDK objects are created: `speech_config` (SpeechConfig), `audio_in` (AudioConfig), `audio_out` (AudioOutputConfig), `recognizer` (SpeechRecognizer), and `synthesizer` (SpeechSynthesizer). Setting the voice name is a property assignment, not a new object. |
| 52 | **B** | `SpeechRecognizer` handles listening and transcription (steps i+ii). `SpeechSynthesizer` handles speaking the response (step iv). Step iii is handled by the AI model, outside the Speech SDK. |
| 53 | **B** | With both handlers connected, the `recognizing` event fires with partial results as the user speaks (e.g., "Hello", "Hello world"), then the `recognized` event fires once with the final transcription when the user pauses. |
| 54 | **B** | Using environment variables keeps sensitive credentials like API keys out of source code. This is a security best practice to prevent accidental exposure in version control or logs. |
| 55 | **B** | Each stage uses a different language-related setting: STT uses `speech_recognition_language`, the processing stage is application logic independent of the SDK, and TTS uses `speech_synthesis_voice_name` with a Japanese neural voice. The same subscription and endpoint work for all languages. |

---

## Scoring Guide

| Score | Rating | Recommendation |
|-------|--------|----------------|
| 50-55 | Expert (91-100%) | You have mastered Azure Speech in Foundry Tools. Focus on hands-on practice. |
| 44-49 | Proficient (80-90%) | Strong understanding. Review the questions you missed and revisit edge cases. |
| 38-43 | Competent (69-79%) | Good foundation. Spend more time on code patterns and error handling. |
| 28-37 | Developing (51-68%) | Review the SDK classes, event model, and STT vs TTS differences carefully. |
| 0-27  | Beginning (0-50%) | Start with the fundamentals: SpeechConfig, AudioConfig, SpeechRecognizer, and SpeechSynthesizer. Practice the code patterns. |

---

## Quick Reference: Key Facts for the Exam

| Concept | Detail |
|---------|--------|
| Package | `pip install azure-cognitiveservices-speech` |
| Import | `import azure.cognitiveservices.speech as speechsdk` |
| Config | `SpeechConfig(subscription=key, endpoint=url)` |
| STT Input | `AudioConfig(use_default_microphone=True)` |
| TTS Output | `AudioOutputConfig(use_default_speaker=True)` |
| STT Class | `SpeechRecognizer` |
| TTS Class | `SpeechSynthesizer` |
| Final result event | `recognized` |
| Partial result event | `recognizing` |
| Start listening | `start_continuous_recognition()` |
| Stop listening | `stop_continuous_recognition()` |
| Speak text | `speak_text_async(text).get()` |
| Success check | `ResultReason.SynthesizingAudioCompleted` |
| Failure check | `ResultReason.Canceled` |
| Error details | `result.cancellation_details.error_details` |
| Voice property | `speech_config.speech_synthesis_voice_name` |
| Acoustic model | Audio -> Phonemes |
| Language model | Phonemes -> Words |
| Batch transcription | Stored files, async, best-effort |
| Voice Live | Speech-capable agents |
