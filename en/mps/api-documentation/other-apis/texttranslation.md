# TextTranslation

## 1. API Description

Domain name for API request: mps.intl.tencentcloudapi.com.

This API is used to translate text.

A maximum of 5 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://www.tencentcloud.com/document/api/1041/33628).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/1041/33628). The value used for this API: TextTranslation. |
| Version | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/1041/33628). The value used for this API: 2019-06-12. |
| Region | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/1041/33628). For more information, please see the [list of regions](https://www.tencentcloud.com/document/api/1041/33628#region-list) supported by the product. This API only supports: ap-singapore. |
| SourceText | Yes | String | Text to be translated, which must be encoded in UTF-8 format. Characters not encoded in UTF-8 format cannot be translated. Input valid text. Unconventional content, such as HTML tags, may also cause translation failures. The text length per request must be less than 2,000 characters. |
| Source | Yes | String | Source language. Valid values:     "auto": "automatic recognition (recognized as a language).",     "ab": "Abkhaz language.",     "ace": Acehnese.",     "ach": "Acholi.",     "af": "Afrikaans.",     "ak": "Twi (Akan).",     "am": "Amharic",     "ar": "Arabic.",     "as": "Assamese.",     "ay": "Aymara.",     "az": "Azerbaijani.",     "ba": "Bashkir.",     "ban": "Balinese",     "bbc": "Batak Toba.",     "bem": "Bemba",     "bew": "Betawi",     "bg": "Bulgarian.",     "bho": "Bhojpuri.",     "bik": "Bikol",     "bm": "Bambara.",     "bn": "Bengali.",     "br": "Breton.",     "bs": "Bosnian.",     "btx": "Batak Karo.",     "bts": "Batak Simalungun.",     "bua": "Buryat.",     "ca": "Catalan.",     "ceb": "Cebuano.",     "cgg": "Kiga",     "chm": "Meadow Mari language.",     "ckb": "Kurdish (Sorani).",     "cnh": "Hakha Chin.",     "co": "Corsican.",     "crh": "Crimean Tatar.",     "crs": "Seychellois Creole.",     "cs": "Czech.",     "cv": "Chuvash.",     "cy": "Welsh.",     "da": "Danish.",     "de": "German.",     "din": "Dinka",     "doi": "Dogri.",     "dov": "Dombe.",     "dv": "Divehi.",     "dz": "Dzongkha.",     "ee": "Ewe",     "el": "Greek.",     "en": "English.",     "eo": "Esperanto.",     "es": "Spanish.",     "et": "Estonian.",     "eu": "Basque.",     "fa": "Persian.",     "ff": "Fula.",     "fi": "Finnish.",     "fil": "Filipino (Tagalog).",     "fj": "Fijian.",     "fr": "French.",     "fr-CA": "French (Canada).",     "fr-FR": "French (France).",     "fy": "Frisian.",     "ga": "Irish.",     "gaa": "Ga.",     "gd": "Scottish Gaelic.",     "gl": "Galician.",     "gn": "Guarani.",     "gom": "Goan Konkani.",     "gu": "Gujarati.",     "gv": "Manx.",     "ha": "Hausa",     "haw": "Hawaiian.",     "he": "Hebrew.",     "hi": "Hindi.",     "hil": "Hiligaynon.",     "hmn": "Hmong.",     "hr": "Croatian.",     "hrx": "Hunsrik.",     "ht": "Haitian Creole.",     "hu": "Hungarian.",     "hy": "Armenian.",     "id": "Indonesian.",     "ig": "Igbo",     "ilo": "Iloko.",     "is": "Icelandic.",     "it": "Italian.",     "iw": "Hebrew.",     "ja": "Japanese.",     "jv": "Javanese.",     "jw": "Javanese.",     "ka": "Georgian.",     "kk": "Kazakh.",     "km": "Khmer.",     "kn": "Kanada.",     "ko": "Korean.",     "kri": "Krio",     "ku": "Kurdish (Kurmanji).",     "ktu": "Kituba.",     "ky": "Kirghiz.",     "la": "Latin.",     "lb": "Luxembourgish.",     "lg": "Ganda (Luganda).",     "li": "Limburgish.",     "lij": "Ligurian.",     "lmo": "Lombard.",     "ln": "Lingala.",     "lo": "Lao.",     "lt": "Lithuanian.",     "ltg": "Latgalian.",     "luo": "Luo",     "lus": "Mizo.",     "lv": "Latvian.",     "mai": "Maithili.",     "mak": "Makassar.",     "mg": "Malagasy.",     "mi": "Maori.",     "min": "Minangkabau.",     "mk": "Macedonian.",     "ml": "Malayalam.",     "mn": "Mongolian.",     "mr": "Marathi.",     "ms": "Malay.",     "mt": "Maltese.",     "my": "Burmese.",     "ne": "Nepali.",     "new": "Nepali (Newar).",     "nl": "Dutch.",     "no": "Norwegian.",     "nr": "Ndebele (South).",     "nso": "Northern Sotho (Sepedi).",     "nus": "Nuer.",     "ny": "Chichewa (Nyanja).",     "oc": "Occitan.",     "om": "Oromo",     "or": "Odia (Oria).",     "pa": "Punjabi.",     "pag": "Pangasinan.",     "pam": "Kapampangan.",     "pap": "Papiamento",     "pl": "Polish.",     "ps": "Pashto",     "pt": "Portuguese.",     "pt-BR": "Portuguese (Brazil).",     "pt-PT": "Portuguese (Portugal).",     "qu": "Quechuan.",     "ro": "Romanian.",     "rom": "Romani.",     "rn": "Rundi",     "ru": "Russian.",     "rw": "Kinyarwanda.",     "sa": "Sanskrit.",     "scn": "Sicilian.",     "sd": "Sindhi.",     "sg": "Sango",     "shn": "Shan.",     "si": "Sinhalese.",     "sk": "Slovak.",     "sl": "Slovene.",     "sm": "Samoan.",     "sn": "Shona.",     "so": "Somali.",     "sq": "Albanian.",     "sr": "Serbian.",     "ss": "Swati.",     "st": "Sesotho.",     "su": "Sundanese.",     "sv": "Swedish.",     "sw": "Swahili.",     "szl": "Silesian.",     "ta": "Tamil.",     "te": "Telugu.",     "tet": "Tetum.",     "tg": "Tajik.",     "th": "Thai.",     "ti": "Tigrinya.",     "tk": "Turkmen.",     "tl": " Filipino (Tagalog).",     "tn": "Tswana.",     "tr": "Turkish.",     "ts": "Tsonga.",     "tt": "Tatar.",     "ug": "Uyghur.",     "uk": "Ukrainian.",     "ur": "Urdu.",     "uz": "Uzbek.",     "vi": "Vietnamese.",     "xh": "Xhosa.",     "yi": "Yiddish.",     "yo": "Yoruba.",     "yua": "Yucatec Maya.",     "yue": "Cantonese.",     "zh": "Simplified Chinese.",     "zh-TW": "Chinese (Traditional).",     "zu": "Zulu." |
| Target | Yes | String | Target language. Valid values:     "ab": "Abkhaz language.",     "ace": "Acehnese.",     "ach": "Acholi.",     "af": "Afrikaans.",     "ak": "Twi (Akan).",     "am": "Amharic",     "ar": "Arabic.",     "as": "Assamese.",     "ay": "Aymara.",     "az": "Azerbaijani.",     "ba": "Bashkir.",     "ban": "Balinese",     "bbc": "Batak Toba.",     "bem": "Bemba",     "bew": "Betawi",     "bg": "Bulgarian.",     "bho": "Bhojpuri.",     "bik": "Bikol",     "bm": "Bambara.",     "bn": "Bengali.",     "br": "Breton.",     "bs": "Bosnian.",     "btx": "Batak Karo.",     "bts": "Batak Simalungun.",     "bua": "Buryat.",     "ca": "Catalan.",     "ceb": "Cebuano.",     "cgg": "Kiga",     "chm": "Meadow Mari language.",     "ckb": "Kurdish (Sorani).",     "cnh": "Hakha Chin.",     "co": "Corsican.",     "crh": "Crimean Tatar.",     "crs": "Seychellois Creole.",     "cs": "Czech.",     "cv": "Chuvash.",     "cy": "Welsh.",     "da": "Danish.",     "de": "German.",     "din": "Dinka",     "doi": "Dogri.",     "dov": "Dombe.",     "dv": "Divehi.",     "dz": "Dzongkha.",     "ee": "Ewe",     "el": "Greek.",     "en": "English.",     "eo": "Esperanto.",     "es": "Spanish.",     "et": "Estonian.",     "eu": "Basque.",     "fa": "Persian.",     "ff": "Fula.",     "fi": "Finnish.",     "fil": "Filipino (Tagalog).",     "fj": "Fijian.",     "fr": "French.",     "fr-CA": "French (Canada).",     "fr-FR": "French (France).",     "fy": "Frisian.",     "ga": "Irish.",     "gaa": "Ga.",     "gd": "Scottish Gaelic.",     "gl": "Galician.",     "gn": "Guarani.",     "gom": "Goan Konkani.",     "gu": "Gujarati.",     "gv": "Manx.",     "ha": "Hausa",     "haw": "Hawaiian.",     "he": "Hebrew.",     "hi": "Hindi.",     "hil": "Hiligaynon.",     "hmn": "Hmong.",     "hr": "Croatian.",     "hrx": "Hunsrik.",     "ht": "Haitian Creole.",     "hu": "Hungarian.",     "hy": "Armenian.",     "id": "Indonesian.",     "ig": "Igbo",     "ilo": "Iloko.",     "is": "Icelandic.",     "it": "Italian.",     "iw": "Hebrew.",     "ja": "Japanese.",     "jv": "Javanese.",     "jw": "Javanese.",     "ka": "Georgian.",     "kk": "Kazakh.",     "km": "Khmer.",     "kn": "Kanada.",     "ko": "Korean.",     "kri": "Krio",     "ku": "Kurdish (Kurmanji).",     "ktu": "Kituba.",     "ky": "Kirghiz.",     "la": "Latin.",     "lb": "Luxembourgish.",     "lg": "Ganda (Luganda).",     "li": "Limburgish.",     "lij": "Ligurian.",     "lmo": "Lombard.",     "ln": "Lingala.",     "lo": "Lao.",     "lt": "Lithuanian.",     "ltg": "Latgalian.",     "luo": "Luo",     "lus": "Mizo.",     "lv": "Latvian.",     "mai": "Maithili.",     "mak": "Makassar.",     "mg": "Malagasy.",     "mi": "Maori.",     "min": "Minangkabau.",     "mk": "Macedonian.",     "ml": "Malayalam.",     "mn": "Mongolian.",     "mr": "Marathi.",     "ms": "Malay.",     "mt": "Maltese.",     "my": "Burmese.",     "ne": "Nepali.",     "new": "Nepali (Newar).",     "nl": "Dutch.",     "no": "Norwegian.",     "nr": "Ndebele (South).",     "nso": "Northern Sotho (Sepedi).",     "nus": "Nuer.",     "ny": "Chichewa (Nyanja).",     "oc": "Occitan.",     "om": "Oromo",     "or": "Odia (Oria).",     "pa": "Punjabi.",     "pag": "Pangasinan.",     "pam": "Kapampangan.",     "pap": "Papiamento",     "pl": "Polish.",     "ps": "Pashto",     "pt": "Portuguese.",     "pt-BR": "Portuguese (Brazil).",     "pt-PT": "Portuguese (Portugal).",     "qu": "Quechuan.",     "ro": "Romanian.",     "rom": "Romani.",     "rn": "Rundi",     "ru": "Russian.",     "rw": "Kinyarwanda.",     "sa": "Sanskrit.",     "scn": "Sicilian.",     "sd": "Sindhi.",     "sg": "Sango",     "shn": "Shan.",     "si": "Sinhalese.",     "sk": "Slovak.",     "sl": "Slovene.",     "sm": "Samoan.",     "sn": "Shona.",     "so": "Somali.",     "sq": "Albanian.",     "sr": "Serbian.",     "ss": "Swati.",     "st": "Sesotho.",     "su": "Sundanese.",     "sv": "Swedish.",     "sw": "Swahili.",     "szl": "Silesian.",     "ta": "Tamil.",     "te": "Telugu.",     "tet": "Tetum.",     "tg": "Tajik.",     "th": "Thai.",     "ti": "Tigrinya.",     "tk": "Turkmen.",     "tl": " Filipino (Tagalog).",     "tn": "Tswana.",     "tr": "Turkish.",     "ts": "Tsonga.",     "tt": "Tatar.",     "ug": "Uyghur.",     "uk": "Ukrainian.",     "ur": "Urdu.",     "uz": "Uzbek.",     "vi": "Vietnamese.",     "xh": "Xhosa.",     "yi": "Yiddish.",     "yo": "Yoruba.",     "yua": "Yucatec Maya.",     "yue": "Cantonese.",     "zh": "Simplified Chinese.",     "zh-TW": "Chinese (Traditional).",     "zu": "Zulu." |
| UserExtPara | No | String | User extension parameter. |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| TargetText | String | Text after translation. |
| Source | String | Source language. See the input parameter Source. |
| Target | String | Target language. See the input parameter Target. |
| RequestId | String | The unique request ID, generated by the server, will be returned for every request (if the request fails to reach the server for other reasons, the request will not obtain a RequestId). RequestId is required for locating a problem. |

## 4. Example

### Example1 Text Translation Request Example

#### Input Example

```
POST / HTTP/1.1
Host: mps.intl.tencentcloudapi.com
Content-Type: application/json
X-TC-Action: TextTranslation
<Common request parameters>

{
    "SourceText": "hello",
    "Source": "zh",
    "Target": "en"
}
```

#### Output Example

```json
{
    "Response": {
        "RequestId": "6411c585-ee14-4a53-8642-dea0f16e161d",
        "Source": "zh",
        "Target": "en",
        "TargetText": "hello"
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
| InvalidParameterValue.SourceLanguage | SourceLanguage parameter error. |
| InvalidParameterValue.SourceText | A SourceText parameter error occurs. |
| InvalidParameterValue.TextContent | A TextContent parameter value error occurs. |
| InvalidParameterValue.TranslateDstLanguage | The value of the target language parameter is incorrect. |
| ResourceNotFound.UserUnregister | The user is not registered. |
| UnsupportedOperation.TextTooLong | The text for a single request exceeds the length limit. |


---
*Source: [https://www.tencentcloud.com/document/product/1041/75936](https://www.tencentcloud.com/document/product/1041/75936)*
