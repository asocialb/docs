# CreateSmartSubtitleTemplate

## 1. API Description

Domain name for API request: mps.intl.tencentcloudapi.com.

This API is used to create a custom smart subtitle template.

A maximum of 20 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://www.tencentcloud.com/document/api/1041/33628).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/1041/33628). The value used for this API: CreateSmartSubtitleTemplate. |
| Version | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/1041/33628). The value used for this API: 2019-06-12. |
| Region | No | String | [Common Params](https://www.tencentcloud.com/document/api/1041/33628). This parameter is not required for this API. |
| Name | Yes | String | Smart subtitle template name. Length limit: 64 characters. |
| VideoSrcLanguage | Yes | String | Source language of the video with smart subtitles. OCR recognition only supports the following languages: `zh_en`: Chinese and English. `multi`: others. ASR recognition and pure subtitle translation currently support the following languages: `auto`: automatic recognition (it is only supported in pure subtitle translation). `zh`: Simplified Chinese. `en`: English. `ja`: Japanese. `ko`: Korean. `zh-PY`: Chinese, English, and Cantonese. `zh_medical`: Chinese (medical scenario). `vi`: Vietnamese. `ms`: Malay. `id`: Indonesian. `fil`: Filipino. `th`: Thai. `pt`: Portuguese. `tr`: Turkish. `ar`: Arabic. `es`: Spanish. `hi`: Hindi. `fr`: French. `de`: German. `it`: Italian. `zh_dialect`: Chinese dialect. `zh_en`: Chinese and English. `yue`: Cantonese. `ru`: Russian. `prime_zh`: Chinese, English, and Chinese dialects. `af-ZA`: Afrikaans (South Africa). `sq-AL`: Albanian (Albania). `am-ET`: Amharic (Ethiopia). `ar-DZ`: Arabic (Algeria). `ar-BH`: Arabic (Bahrain). `ar-EG`: Arabic (Egypt). `ar-IQ`: Arabic (Iraq). `ar-IL`: Arabic (Israel). `ar-JO`: Arabic (Jordan). `ar-KW`: Arabic (Kuwait). `ar-LB`: Arabic (Lebanon). `ar-MR`: Arabic (Mauritania). `ar-MA`: Arabic (Morocco). `ar-OM`: Arabic (Oman). `ar-QA`: Arabic (Qatar). `ar-SA`: Arabic (Saudi Arabia). `ar-PS`: Arabic (State of Palestine). `ar-SY`: Arabic (Syria). `ar-TN`: Arabic (Tunisia). `ar-AE`: Arabic (United Arab Emirates). `ar-YE`: Arabic (Yemen). `hy-AM`: Armenian (Armenia). `az-AZ`: Azerbaijani (Azerbaijan). `eu-ES`: Basque (Spain). `bn-BD`: Bengali (Bangladesh). `bn-IN`: Bengali (India). `bs-BA`: Bosnian (Bosnia and Herzegovina). `bg-BG`: Bulgarian (Bulgaria). `my-MM`: Burmese (Myanmar). `ca-ES`: Catalan (Spain). `hr-HR`: Croatian (Croatia). `cs-CZ`: Czech (Czech Republic). `da-DK`: Danish (Denmark). `nl-BE`: Dutch (Belgium). `nl-NL`: Dutch (Holland). `en-AU`: English (Australia). `en-CA`: English (Canada). `en-GH`: English (Ghana). `en-HK`: English (Hong Kong (China)). `en-IN`: English (India). `en-IE`: English (Ireland). `en-KE`: English (Kenya). `en-NZ`: English (New Zealand). `en-NG`: English (Nigeria). `en-PK`: English (Pakistan). `en-PH`: English (Philippines). `en-SG`: English (Singapore). `en-ZA`: English (South Africa). `en-TZ`: English (Tanzania). `en-GB`: English (UK). `en-US`: English (US). `et-EE`: Estonian (Estonia). `fil-PH`: Filipino (Philippines). `fi-FI`: Finnish (Finland). `fr-BE`: French (Belgium). `fr-CA`: French (Canada). `fr-FR`: French (France). `fr-CH`: French (Switzerland). `gl-ES`: Galician (Spain). `ka-GE`: Georgian (Georgia). `el-GR`: Greek (Greece). `gu-IN`: Gujarati (India). `iw-IL`: Hebrew (Israel). `hi-IN`: Hindi (India). `hu-HU`: Hungarian (Hungary). `is-IS`: Icelandic (Iceland). `id-ID`: Indonesian (Indonesia). `it-IT`: Italian (Italy). `it-CH`: Italian (Switzerland). `ja-JP`: Japanese (Japan). `jv-ID`: Javanese (Indonesia). `kn-IN`: Kannada (India). `kk-KZ`: Kazakh (Kazakhstan). `km-KH`: Khmer (Cambodia). `rw-RW`: Kinyarwanda (Rwanda). `ko-KR`: Korean (South Korea). `lo-LA`: Lao (Laos). `lv-LV`: Latvian (Latvia). `lt-LT`: Lithuanian (Lithuania). `mk-MK`: Macedonian (North Macedonia). `ms-MY`: Malay (Malaysia). `ml-IN`: Malayalam (India). `mr-IN`: Marathi (India). `mn-MN`: Mongolian (Mongolia). `ne-NP`: Nepali (Nepal). `no-NO`: Bokmal Norwegian (Norway). `fa-IR`: Persian (Iran). `pl-PL`: Polish (Poland). `pt-BR`: Portuguese (Brazil). `pt-PT`: Portuguese (Portugal). `ro-RO`: Romanian (Romania). `ru-RU`: Russian (Russia). `sr-RS`: Serbian (Serbia). `si-LK`: Sinhalese (Sri Lanka). `sk-SK`: Slovak (Slovakia). `sl-SI`: Slovenian (Slovenia). `st-ZA`: Sesotho (South Africa). `es-AR`: Spanish (Argentina). `es-BO`: Spanish (Bolivia). `es-CL`: Spanish (Chile). `es-CO`: Spanish (Colombia). `es-CR`: Spanish (Costa Rica). `es-DO`: Spanish (Dominican Republic). `es-EC`: Spanish (Ecuador). `es-SV`: Spanish (El Salvador). `es-GT`: Spanish (Guatemala). `es-HN`: Spanish (Honduras). `es-MX`: Spanish (Mexico). `es-NI`: Spanish (Nicaragua). `es-PA`: Spanish (Panama). `es-PY`: Spanish (Paraguay). `es-PE`: Spanish (Peru). `es-PR`: Spanish (Puerto Rico). `es-ES`: Spanish (Spain). `es-US`: Spanish (US). `es-UY`: Spanish (Uruguay). `es-VE`: Spanish (Venezuela). `su-ID`: Sundanese (Indonesia). `sw-KE`: Swahili (Kenya). `sw-TZ`: Swahili (Tanzania). `sv-SE`: Swedish (Sweden). `ta-IN`: Tamil (India). `ta-MY`: Tamil (Malaysia). `ta-SG`: Tamil (Singapore). `ta-LK`: Tamil (Sri Lanka). `te-IN`: Telugu (India). `th-TH`: Thai (Thailand). `ts-ZA`: Tsonga (South Africa). `tr-TR`: Turkish (Turkey). `uk-UA`: Ukrainian (Ukraine). `ur-IN`: Urdu (India). `ur-PK`: Urdu (Pakistan). `uz-UZ`: Uzbek (Uzbekistan). `ve-ZA`: Venda (South Africa). `vi-VN`: Vietnamese (Vietnam). `xh-ZA`: Xhosa (South Africa). `zu-ZA`: Zulu (South Africa). |
| SubtitleType | Yes | Integer | Smart subtitle language type. 0: source language 1: target language 2: source language + target language The value can only be 0 when TranslateSwitch is set to OFF. The value can only be 1 or 2 when TranslateSwitch is set to ON. |
| Comment | No | String | Smart subtitle template description. Length limit: 256 characters. |
| SubtitleFormat | No | String | Smart subtitle file format: - Under the ASR recognition and translation processing type:      - vtt: WebVTT format subtitle.      - srt: SRT format subtitle.      - Unspecified or left blank: no subtitle file generated. - Under the pure subtitle translation processing type:     - original: consistent with the source file.     - vtt: WebVTT format subtitle.     - srt: SRT format subtitle. - Under the OCR recognition and translation processing type:      - vtt: WebVTT format subtitle.      - srt: SRT format subtitle. **Note**: - For ASR recognition mode, when 2 or more languages are involved in translation, this field cannot be unspecified or left blank. - For pure subtitle translation and OCR recognition mode, this field cannot be unspecified or left blank. |
| AsrHotWordsConfigure | No | [AsrHotWordsConfigure](https://www.tencentcloud.com/document/api/1041/33690#AsrHotWordsConfigure) | ASR hotword lexicon parameter. |
| TranslateSwitch | No | String | Subtitle translation switch. `ON`: translation enabled. `OFF`: translation disabled. **Note**: For pure subtitle translation mode, the default value is enabled if the field is unspecified. The field cannot be left blank or set to `OFF`. |
| TranslateDstLanguage | No | String | Target language for subtitle translation. This parameter takes effect when the value of TranslateSwitch is ON. Valid translation languages:`ab`: Abkhazian.`ace`: Acehnese.`ach`: Acholi.`af`: Afrikaans.`ak`: Twi (Akan).`am`: Amharic.`ar`: Arabic.`as`: Assamese.`ay`: Aymara.`az`: Azerbaijani.`ba`: Bashkir.`ban`: Balinese.`bbc`: Batak toba.`bem`: Bemba.`bew`: Betawi.`bg`: Bulgarian.`bho`: Bhojpuri.`bik`: Bikol.`bm`: Bambara.`bn`: Bengali.`br`: Breton.`bs`: Bosnian.`btx`: Batak Karo.`bts`: Batak Simalungun.`bua`: Buryat.`ca`: Catalan.`ceb`: Cebuano.`cgg`: Kiga.`chm`: Meadow Mari.`ckb`: Kurdish (Sorani).`cnh`: Hakha Chin.`co`: Corsican.`crh`: Crimean Tatar.`crs`: Seychellois Creole.`cs`: Czech.`cv`: Chuvash.`cy`: Welsh.`da`: Danish.`de`: German.`din`: Dinka.`doi`: Dogri.`dov`: Dombe.`dv`: Dhivehi.`dz`: Dzongkha.`ee`: Ewe.`el`: Greek.`en`: English.`eo`: Esperanto.`es`: Spanish.`et`: Estonian.`eu`: Basque.`fa`: Persian.`ff`: Fulah.`fi`: Finnish.`fil`: Filipino (Tagalog).`fj`: Fijian.`fr`: French.`fr-CA`: French (Canada).`fr-FR`: French (France).`fy`: Frisian.`ga`: Irish.`gaa`: Ga. `gd`: Scottish Gaelic.`gl`: Galician.`gn`: Guarani.`gom`: Konkani.`gu`: Gujarati.`gv`: Manx.`ha`: Hausa.`haw`: Hawaiian.`he`: Hebrew.`hi`: Hindi.`hil`: Hiligaynon.`hmn`: Hmong.`hr`: Croatian.`hrx`: Hunsrik.`ht`: Haitian Creole.`hu`: Hungarian.`hy`: Armenian.`id`: Indonesian.`ig`: Igbo.`ilo`: Iloko.`is`: Icelandic.`it`: Italian.`iw`: Hebrew.`ja`: Japanese.`jv`: Javanese.`ka`: Georgian.`kk`: Kazakh.`km`: Khmer.`kn`: Kannada.`ko`: Korean.`kri`: Krio.`ku`: Kurdish (Kurmanji).`ktu`: Kituba.`ky`: Kyrgyz.`la`: Latin.`lb`: Luxembourgish.`lg`: Ganda (Luganda).`li`: Limburgish.`lij`: Ligurian.`lmo`: Lombard.`ln`: Lingala.`lo`: Lao.`lt`: Lithuanian.`ltg`: Latgalian.`luo`: Luo.`lus`: Mizo.`lv`: Latvian.`mai`: Maithili.`mak`: Makasar.`mg`: Malagasy.`mi`: Maori.`min`: Minangkabau.`mk`: Macedonian.`ml`: Malayalam.`mn`: Mongolian.`mr`: Marathi.`ms`: Malay.`mt`: Maltese.`my`: Burmese.`ne`: Nepali.`new`: Newari.`nl`: Dutch.`no`: Norwegian.`nr`: Southern Ndebele.`nso`: Northern Sotho (Sepedi).`nus`: Nuer.`ny`: Chichewa (Nyanja).`oc`: Occitan.`om`: Oromo.`or`: Odia.`pa`: Punjabi.`pag`: Pangasinan.`pam`: Kapampangan.`pap`: Papiamento.`pl`: Polish.`ps`: Pashto.`pt`: Portuguese.`pt-BR`: Portuguese (Brazil).`pt-PT`: Portuguese (Portugal).`qu`: Quechua.`ro`: Romanian.`rom`: Romani.`rn`: Rundi.`ru`: Russian.`rw`: Kinyarwanda.`sa`: Sanskrit.`scn`: Sicilian.`sd`: Sindhi.`sg`: Sango.`shn`: Shan.`si`: Sinhala.`sk`: Slovak.`sl`: Slovenian.`sm`: Samoan.`sn`: Shona.`so`: Somali.`sq`: Albanian.`sr`: Serbian.`ss`: Swazi.`st`: Southern Sotho.`su`: Sundanese.`sv`: Swedish.`sw`: Swahili.`szl`: Silesian.`ta`: Tamil.`te`: Telugu.`tet`: Tetum.`tg`: Tajik.`th`: Thai.`ti`: Tigrinya.`tk`: Turkmen.`tn`: Tswana.`tr`: Turkish.`ts`: Tsonga.`tt`: Tatar.`ug`: Uyghur.`uk`: Ukrainian.`ur`: Urdu.`uz`: Uzbek.`vi`: Vietnamese.`xh`: Xhosa.`yi`: Yiddish.`yo`: Yoruba.`yua`: Yucatec Maya.`yue`: Cantonese.`zh`: Chinese (Simplified).`zh-TW`: Chinese (Traditional).`zu`: Zulu.**Note**: Use `/` to separate multiple languages, such as `en/ja`, which indicates English and Japanese. |
| ProcessType | No | Integer | Subtitle processing type. - 0: ASR recognition subtitle. - 1: pure subtitle translation. - 2: OCR recognition subtitle. **Note**: The default processing type is ASR recognition subtitle if the field is unspecified. |
| SelectingSubtitleAreasConfig | No | [SelectingSubtitleAreasConfig](https://www.tencentcloud.com/document/api/1041/33690#SelectingSubtitleAreasConfig) | Area configurations for the subtitle OCR extraction box. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | Unique identifier of the smart subtitle template. |
| RequestId | String | The unique request ID, generated by the server, will be returned for every request (if the request fails to reach the server for other reasons, the request will not obtain a RequestId). RequestId is required for locating a problem. |

## 4. Example

### Example1 Creating a Template

#### Input Example

```
POST / HTTP/1.1
Host: mps.intl.tencentcloudapi.com
Content-Type: application/json
X-TC-Action: CreateSmartSubtitleTemplate
<Common request parameters>

{
    "Name": "Example"
    "VideoSrcLanguage": "zh",
    "SubtitleType": 0
}
```

#### Output Example

```json
{
    "Response": {
        "Definition": 202281,
        "RequestId": "42dc919b-2ec7-412c-85f0-88f003813d04"
    }
}
```

## 5. Developer Resources

### SDK

TencentCloud API 3.0 integrates SDKs that support various programming languages to make it easier for you to call APIs.

Tencent Cloud SDK 3.0 for Python
Tencent Cloud SDK 3.0 for Java
Tencent Cloud SDK 3.0 for PHP
Tencent Cloud SDK 3.0 for Go
Tencent Cloud SDK 3.0 for Node.js
Tencent Cloud SDK 3.0 for .NET
Tencent Cloud SDK 3.0 for C++

### Command Line Interface

Tencent Cloud CLI 3.0

## 6. Error Code

The following only lists the error codes related to the API business logic. For other error codes, see [Common Error Codes](https://www.tencentcloud.com/document/api/1041/33691#common-error-codes).

| Error Code | Description |
| --- | --- |
| InvalidParameterValue.AsrHotWordsConfigure | The value of the hotword lexicon configuration parameter is incorrect. |
| InvalidParameterValue.AsrHotWordsLibraryId | The value of the hotword lexicon ID parameter is incorrect. |
| InvalidParameterValue.AsrHotWordsSwitch | The value of the hotword lexicon switch parameter is incorrect. |
| InvalidParameterValue.Comment | Parameter error: template description. |
| InvalidParameterValue.Name | Incorrect parameter value: `Name` exceeds the length limit. |
| InvalidParameterValue.SubtitleFormat | Incorrect parameter value: The value of the `SubtitleFormat` parameter is invalid. |
| InvalidParameterValue.SubtitleType | The value of the subtitle language type is incorrect. |
| InvalidParameterValue.TranslateDstLanguage | The value of the target language parameter is incorrect. |
| InvalidParameterValue.TranslateSwitch | The value of the translation switch parameter is incorrect. |
| InvalidParameterValue.VideoSrcLanguage | The value of the video source language parameter is incorrect. |


---
*Source: [https://www.tencentcloud.com/document/product/1041/68919](https://www.tencentcloud.com/document/product/1041/68919)*
