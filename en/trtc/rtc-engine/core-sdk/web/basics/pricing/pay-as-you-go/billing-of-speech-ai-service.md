# Billing of Speech AI Service

These billing instructions apply to three services: Speech-to-Text , AI Real-Time Translation and Real-Time Speech Synthesis.

- ââSpeech-to-Text:ââ Transcribes spoken audio into text using Automatic Speech Recognition (ASR/STT). This is commonly used to generate real-time captions.
- ââAI Real-Time Translation:ââ Translates transcribed text into target languages to deliver real-time multilingual subtitles.
- Real-Time Speech Synthesis: Converts text into speech in real-time using TTS (Text to Speech) technology.

### Speech-to-Text

This service recognizes and transcribes audio streams from specified users or all users in a TRTC room.

- This capability is available only to applications subscribed to the [RTC-Engine Monthly Package](https://www.tencentcloud.com/document/product/647/56025).
- For eligible packages (RTC Engine Lite and above), the service is billed on a pay-as-you-go basis after unlocking.
- Third-party STT is not supported in AI Real-Time Translation scenarios to ensure consistency and output quality.
- Billing mode: Postpaid.
- Billing cycle: Daily. Specific billing details and the statement issuance time are subject to [Billing Statement](https://console.tencentcloud.com/expense/bill/overview).

### AI Real-Time Translation

This service translates transcribed content into one or more specified target languages in real-time.

- Billing mode: Postpaid.
- Billing cycle: Daily. Specific billing details and the statement issuance time are subject to [Billing Statement](https://console.tencentcloud.com/expense/bill/overview).

### Real-Time Speech Synthesis

This service converts text to natural, fluent speech in real-time, enabling live voice output.

- Billing mode: Postpaid.
- Billing cycle: Daily. Specific billing details and the statement issuance time are subject to [Billing Statement](https://console.tencentcloud.com/expense/bill/overview).

## Pricing

The following table provides the list prices and language support details for the Speech-to-Text, AI Real-Time Translation and Real-Time Text-to-Speech services:

| ServiceType | Model Type | Unit Price | Support Languages |
| --- | --- | --- | --- |
| Speech-to-Text | Standard | 0.02 (USD/Minute) | Supports 22 languages, including:Chinese, Chinese (Traditional), English, Vietnamese, Japanese, Korean, Indonesian, Thai, Portuguese, Turkish, Arabic, Spanish, Hindi, French, Malay, Filipino, German, Italian, Russian, Swedish, Danish, and Norwegian. If additional language support is required, please contact sales or submit a [support ticket](https://trtc.io/contact). |
| AI Real-Time Translation | Standard | 0.016 (USD/Minute) | Supports 15 languages, including: Chinese, English, Vietnamese, Japanese, Korean, Indonesian, Thai, Portuguese, Arabic, Spanish, French, Malay, German, Italian, and Russian.If additional language support is required, please contact sales or submit a [support ticket](https://trtc.io/contact). |
| Real-Time Speech Synthesis | Flash | 0.06 (USD/1,000 characters) | Supports Chinese, English, Japanese, Korean, and Cantonese (dialect). |
|  | Multilingual model |  | Please contact sales or submit a [support ticket](https://trtc.io/contact) for additional languages. |

## Metering & Usage Notes

> **Note:**Speech-to-Text and AI Real-Time Translation Service duration is metered in seconds and accumulated on a per SDKAppID basis. For billing, the total daily seconds are converted to minutes, and any remaining seconds are rounded up to the next full minute.When Speech-to-Text or AI Real-Time Translation is enabled in a TRTC room, a robot will join as a virtual participant to subscribe to the relevant audio/video streams. This subscription incurs [audio and video usage duration](https://trtc.io/document/42734?product=pricing&menulabel=core%20sdk#).Billing for the Real-Time Speech Synthesis is based on the daily cumulative character count, measured at the character level. The pricing unit is 1,000 characters, calculated to three decimal places.For Speech Synthesis (TTS) billing, the character count is calculated as follows: each Chinese character (including Japanese Kanji, Korean Hanja, and other CJK ideographs) counts as 2 characters. All other charactersâincluding English letters, characters from other languages, punctuation marks, symbols, spaces, and line breaksâcount as 1 character.Speech-to-Text, Real-time Translation, and Real-time Speech Synthesis (integrated in [Conversational AI](https://trtc.io/document/68337?product=conversationalai)) have a concurrency limit of 100. For Real-time Speech Synthesis in other scenarios, the limit is 20 QPS. Please contact sales or submit a [support ticket](https://trtc.io/contact) if you require higher concurrency.

### Speech-to-Text

- Only the duration of audio streams actively undergoing recognition is billed.
- In multi-stream scenarios, the cumulative duration of all input streams is used for billing.
- The system activates the ASR for speech-to-text service only after the user turns on the microphone. The duration matches the length of time the microphone remains active.

### AI Real-Time Translation

- Billed based on the duration of the input audio streams actively translated.
- If a single input stream is translated into multiple target languages, billing is calculated as Input Duration Ã Number of Output Languages

### Real-Time Speech Synthesis

- Usage is measured based on the number of input text characters for real-time speech synthesis.
- For each individual broadcaster stream, charges are applied according to the number of characters that need to be synthesized.

## Billing Examples

All billing figures in the following examples are calculated and rounded to three decimal places.

**Consider the following use case:**

- **Users A and Bï¼**Engage in a conversation in Chinese
- **Viewer C:**  Requires English captions and English speech output
- **Viewer D:**  Requires Japanese captions and Japanese speech output

The system processes the conversation through the following steps:

1. Speech-to-Text  (converting Chinese speech to text)
2. Real-Time Translation (translating text to English and Japanese)
3. Real-Time Speech Synthesis (converting translated text to speech)

**Usage Details:**

- Conversation duration: 10 minutes
- Total text characters: 26 thousand characters (The text character counts in this example are provided for illustrative purposes only)
- User A's English text: 8 thousand characters
- User A's Japanese text: 5 thousand characters
- User B's English text: 8 thousand characters
- User B's Japanese text: 5 thousand characters

**The corresponding charges are calculated as follows:**

| Billing Type | User A | User B | Subtotal |
| --- | --- | --- | --- |
| Speech-to-Text | 10 minutes | 10 minutes | 20 minutes |
| AI Real-Time Translation | 10 minutes Ã 2 | 10 minutes Ã 2 | 40 minutes |
| Real-Time Speech Synthesis | 8 thousand English characters + 5 thousand Japanese characters | 8 thousand English characters + 5 thousand Japanese characters | 26 thousand characters |

- Speech-to-Text charges: 20 minutes of usage is incurred, unit price is 0.020 USD/minute, the cost is 0.020 Ã 20 = 0.4 USD;
- AI Real-Time Translation charges: 40 minutes of usage is incurred, unit price is 0.016 USD/minute, the cost is 0.016 Ã 40 = 0.64 USD.
- Real-Time Speech Synthesis charges: 26.000 thousand characters of usage is incurred, unit price is 0.060 USD/thousand characters, the cost is 0.060 Ã 26 = 1.56 USD

In this scenario, you need to pay the total fee: 2.6 USD.

## Integration Guide

For integration steps, please refer to the [Speech-to-Text and Translation Integration Instructions](https://trtc.io/document/66148?product=rtcengine&menulabel=serverfeaturesapis).

To configure Real-Time Speech Synthesis (TTS) in Conversational AI, refer to [Conversational AI TTS Configuration](https://trtc.io/document/68340?product=conversationalai).


---
*Source: [https://trtc.io/document/67832](https://trtc.io/document/67832)*
