# French News Reader

Paste a link to a French news article and read it with likely B2/C1 words underlined. Hover (desktop) or tap (mobile) a word for its definition. The journalist, publication and a link to the original appear under the headline.

It runs entirely on free services and needs no API key:

- **GitHub Pages** hosts the page (`index.html`).
- **A Cloudflare Worker** (`worker/`) fetches the article page for you. Browsers cannot do this directly.
- **Your browser** extracts the headline, author and text, and picks the words using a word-frequency list.
- **Wiktionary** supplies definitions when you hover or tap.

## Limits

- Paywalled sites such as Le Monde usually return only the teaser to an anonymous fetch. The page warns when the text is short. This app does not try to get around paywalls.
- Levels are estimates from word frequency, not an official CEFR list. Some everyday words get underlined and some useful idioms are missed. Inflected verbs can look rarer than they are.
- Names and capitalised words are never underlined, which also skips rare words at the start of a sentence.
- Definitions come from English Wiktionary. Inflected forms resolve to their base word when Wiktionary marks them that way; otherwise you may see "No definition found for this form."
- Some sites block automated fetching and will return an error.

## Tuning

In `index.html`, `KNOWN_MAX` and `B2_MAX` set which frequency ranks count as everyday, B2 and C1 vocabulary. Raise them to underline fewer words.

## Credits

- Word frequencies: [FrequencyWords](https://github.com/hermitdave/FrequencyWords) by Hermit Dave, from OpenSubtitles, CC BY-SA 4.0.
- Definitions: [Wiktionary](https://en.wiktionary.org), CC BY-SA.
- Article extraction: [Readability.js](https://github.com/mozilla/readability) by Mozilla, Apache 2.0 (`vendor/Readability.js`).