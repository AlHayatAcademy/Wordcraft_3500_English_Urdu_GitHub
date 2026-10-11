# Wordcraft — Newspaper English

A colourful, responsive vocabulary-learning website containing **5,521 words (200 optional Foundation, 1,751 Intermediate, 2,304 Advanced, 1,266 Challenging)** and **3,000 expressions (1,000 phrasal/multiword verbs, 1,000 idioms, 1,000 collocations)**, English and Urdu meanings, examples, pronunciation, quizzes, scheduled review, newspaper excerpts, sentence writing and speaking practice.

## GitHub Pages deployment

The supplied ZIP is ready for a repository root. No npm, framework build, API key or backend is required.

1. Extract the ZIP on your computer.
2. Create a GitHub repository, for example `wordcraft-english`.
3. Upload the **contents** of the extracted folder to the repository root. `index.html` must be at the root, not inside another folder. Keep all JSON and JavaScript files alongside it.
4. Open **Settings → Pages**.
5. Under Build and deployment, choose **Deploy from a branch**, select `main` and `/ (root)`, and save.
6. Wait for GitHub to show the website URL. It normally follows `https://YOUR-USERNAME.github.io/YOUR-REPOSITORY/`.
7. Open the site and begin a daily lesson. Later commits to the selected branch update the website automatically.

The site uses relative asset URLs, so it works under a repository subpath. GitHub hosting availability and account policies remain controlled by GitHub.

## Local use

Use a small local HTTP server rather than double-clicking `index.html`, because browsers often block JSON fetches from `file://` URLs:

```bash
python -m http.server 8000
```

Then open `http://localhost:8000/`. Python is needed only for this optional local preview, not for GitHub deployment.

## Visual design

The redesigned UI uses illustrated violet banners, golden action buttons, teal Intermediate, orange Advanced and purple Challenging cards, colourful recall feedback, responsive layouts and a complete dark theme. Streaks and progress reflect browser-local activity. Learning-path pages show 12 units at a time. Illustration: original AI-generated Wordcraft hero, bundled locally; no image API is needed to run the site.

## Interactive learning cards

Each word and expression has Learn, Examples, Practise, Writing and Speaking tabs, with differently coloured components, pronunciation controls and a sentence notebook. Four blanks practise English meaning recall, Urdu-to-English recall, sentence completion and word combinations. Each offers Check, Hint and Reveal, with a Check all button. Only an unassisted first recall answer updates the review schedule; hinted/revealed answers do not count as independent recall. Answers accept capitalization and extra spaces, but blanks expect the displayed target form rather than arbitrary paraphrases.

Choose a news, everyday conversation or formal-writing scenario, write your own sentence, use the self-review checklist, listen to it and save it. These checks guide practice; they do not claim automatic grammar or meaning assessment. Previous/Next stays within the same level.

## Learning activities

- Learning path: ten-word units, gradual intermediate → advanced → challenging progression; any unit can be explored. A unit is practised when every word has been introduced and answered correctly at least once.
- Library: search English or Urdu; filter learning level, word type, category, publisher and progress.
- Expression studio: English/Urdu meanings, contextual explanations, construction and tone guidance, original examples, pronunciation, recall questions, bookmarks and sentence notebook.
- Urdu meanings: all 5,521 primary learning meanings in Urdu with English beside them; RTL text and Nastaliq font preference.
- Daily lesson: recall first, reveal meaning and example, then rate your recall.
- Practice: meaning multiple choice, contextual gaps, recall/spelling and listening/spelling.
- Usage explorer: selected retained words with multiple original contextual examples, Urdu explanations, collocations and usage tips.
- Reading lab: 148 brief attributed excerpts, highlighted vocabulary and links to publisher articles.
- Sentence studio: your own writing, word-use checks, punctuation hints, a saved notebook and optional voice recording.
- Progress: scheduled review, bookmarks, activity history, export/restore and vocabulary TSV export.
- Light/dark themes, mobile layouts and offline caching after an initial connected visit.

## Word families and explained collocations

`family-lessons.json` enriches every card with available family definitions from the existing bank, direct WordNet derivational/pertainym links, and reviewed original lessons for 91 useful roots (also reused on existing sibling headwords). Members show part of speech, meaning, Urdu where supplied, a sourced or original example where available, audio buttons and a practice blank. Larger families expand behind a labelled control. Different senses and spelling variants remain distinct; plural and verb inflections are not generated as new family members. Some dictionary entries lack an example or Urdu translation; the UI identifies missing examples rather than inventing sentences. This is a documented family collection, not an exhaustive list of every possible derived word.

Explained collocations reuse the existing 1,000-entry studio and 364 reviewed additional combinations/constructions. Meanings, Urdu and original examples accompany each explanation. Unexpanded legacy combinations remain labelled separately; no claim of measured newspaper frequency is made. “Respectively” includes constructions that map parallel lists, with explicit distinctions from respectful and respectable. The review and coverage counts are in `family-review.json`; repeated placements on different root cards are not unique collocations.

Writing provides context choices, sentence/paragraph drafts, basic target/capital/punctuation checks, text-to-speech and notebook saving. Drafts persist during the session; saved sentences persist in backups. Speaking provides listen/repeat practice, register guidance, a 60-second response timer and self-review checklist. It activates no microphone; the existing Sentence studio remains available for local recording and playback. Neither tab automatically grades grammar, meaning, fluency or pronunciation.

Optional content rebuilding: `python3 scripts/build-family-lessons.py /absolute/path/to/wordnet.zip`. Supply Princeton WordNet 3.0; no Python or dictionary download is required to run or deploy the already compiled site.

## Imported vocabulary review

The supplied `al-hayat-aptitudeprep-main/data/vocabulary-bank.json` contains 2,999 unique words. We added 2,021 missing words and skipped 978 existing words, comparing case-insensitively after collapsing whitespace. Existing entries and progress IDs were preserved; new IDs are 6117–8137. The original three levels remain the default learning route; 200 imported Foundation words are optional.

All imported entries received an editorial review of meanings, Urdu, part of speech, example sense, synonyms, antonyms, collocations and genuine word families. Source review flags were not accepted as evidence. Unsuitable opposites and unrelated families were removed; empty lists have explanatory notes rather than invented items. Machine-generated IPA was excluded. Imported examples are labelled separately from newspaper quotations and WordNet examples. Source claims remain unverified unless explicitly documented in the review. `import-review.json` contains the review record; `import-audit.csv` records each added word and changed fields. No licence was supplied for the imported bank; its inclusion does not establish third-party reuse rights.

## Source methodology

The original newspaper-observed collection is drawn from an accessible sample of 148 articles, spanning 25 February 2023–10 October 2026:

| Publisher | Articles |
|---|---:|
| DAWN |90|
| The Guardian |26|
| VOA Learning English |24|
| The Independent |8|

The sample contains approximately 94,902 extracted text tokens. Some retrieved articles contain only partial text. This is **not an exhaustive scan of every newspaper edition**, and the ranks are **sample frequencies**, not a proven ranking of the most frequent English words worldwide or of the complete DAWN archive.

Rank first considers article prevalence, then total occurrences. Common grammatical words, proper names, abbreviations and retrieval noise were filtered. Inflections were partly grouped; entries represent written words rather than strictly independent word families. `count` and `articles` reflect the retrieved sample and automated processing.

Princeton WordNet 3.0 supplies dictionary meanings and reusable examples. Original learning definitions and examples correct many unsuitable first senses and fill gaps. Urdu meanings have been written for each primary learning meaning. Selected words have additional contextual Urdu in Usage explorer.

The revised collection removes beginner words and redundant forms, then adds curated intermediate, advanced and challenging vocabulary to reach the requested level counts. Supplemental entries carry `origin: supplemental`, have zero sample frequency and no invented article evidence. Levels are editorial guidance, not certified CEFR classifications. Each retained word has a contextual explanation, a natural collocation and a usage tip.

Expressions are a curated collection for newspaper reading and functional English; **“top” is not a measured frequency ranking**. Examples and expanded explanations are original learning content. Phrasal/multiword verbs include accurately labelled particle and prepositional constructions. Idioms have register guidance so informal expressions are not presented as suitable for every formal context.

Each publisher article contributes only one short excerpt of at most 23 space-separated words to Reading lab. Full article text, internal research corpora and search retrieval dumps are **not** included. Newspaper excerpts retain publisher rights and are clearly attributed. The source evidence index is in the site’s About section and `sources.json`.

## Progress and privacy

Progress is stored in browser localStorage under `wordcraft-v1`. It is device/browser specific and does not sync automatically. Clearing browser data can remove it. Export backups regularly and restore them on another device.

Microphone recording begins only when you click Record and grant browser permission. Recordings stay on the current page and can be downloaded; they are not uploaded. Stop and download before navigating away. Browser speech voices and microphone support vary by device. Optional short sound effects use Web Audio, start off, and play only after user actions. Toggle Sounds in the header; the setting is saved with progress. There are no external audio files or autoplay music.

The writing checker tests target word usage, length, initial capital and closing punctuation. It is **not** an AI grammar, semantics or factual-accuracy checker. No automatic pronunciation assessment is provided. “Retained” is a local progress indicator requiring a stage of at least 4 and 3 correct quiz answers; it is not a certified proficiency measure.

The static site does not scrape or automatically fetch new newspaper articles. Updates to learning content require editing the JSON data and redeploying. External Google Fonts are optional; system fallback fonts work when unavailable. No external tracking scripts are included.

## Content files

| File | Purpose |
|---|---|
|`index.html`|Application shell|
|`style.css`|Base responsive design and Urdu styles|
|`design.css`|Vibrant theme, mobile and dark-mode overrides|
|`design.js`|Redesigned home, learning path and page banners|
|`cards.js`, `cards.css`|Colour-coded cards, four blank exercises and functional writing|
|`family-lessons.json`, `family-authored.json`, `family-review.json`|Expanded families, explained combinations and provenance|
|`scripts/build-family-lessons.py`|Optional content-generation script|
|`import-review.json`, `import-audit.csv`|Import provenance, editorial review and added-word audit|
|`assets/wordcraft-hero.png`|Bundled hero illustration|
|`app.js`|Learning screens, quizzes, progress and export/restore|
|`data.json`|5,521 levelled entries, explanations, collocations and guidance|
|`enhancements.js`|Learning path, expression studio and optional audio feedback|
|`expressions.json`|3,000 detailed expression lessons|
|`sources.json`|Publisher links, dates and short excerpts|
|`usage.json`|Contextual usage lessons (only retained words shown)|
|`meta.json`|Sample information and WordNet licence|
|`sw.js`|Offline caching|
|`manifest.json`|App metadata|
|`favicon.svg`|Vector icon|
|`.nojekyll`|Disable Jekyll processing on GitHub Pages|

For a major content change, increment the cache name in `sw.js` and keep word IDs stable to preserve existing progress.

## Competitor design review

Public documentation, not paid-account testing, informed the design:

- Vocabulary.com: adaptive word practice and timely revisiting — https://www.vocabulary.com/how-it-works/
- Quizlet Learn: goals and multiple question types — https://help.quizlet.com/hc/en-us/articles/360030986971-Studying-with-Learn
- Anki: recall before revealing, review queues and self-ratings — https://docs.ankiweb.net/manual/studying
- British Council: learner-oriented vocabulary activities — https://learnenglish.britishcouncil.org/free-resources/vocabulary
- British Council: separable/inseparable phrasal verb guidance — https://learnenglish.britishcouncil.org/free-resources/grammar/b1-b2/phrasal-verbs
- Cambridge: collocations and register awareness — https://dictionary.cambridge.org/grammar/british-grammar/using-english

This implementation uses a simple increasing-interval scheduler. It does not reproduce Anki FSRS or any proprietary adaptive engine, and no claim of superior learning outcomes is made.

## Verification

Run the included functional checks with Node.js (no packages required):

```bash
node tests/qa.cjs
```


Checks: JavaScript syntax, all 5,521 unique words and 3,000 unique expressions, exact level/type counts, imported words in search/lessons/quizzes, new-ID backup restore, four blanks per entry, assisted-answer handling, Writing/Speaking tabs, family recall marking, timer completion, draft retention, unique card field IDs, nonempty English/Urdu meanings and examples, source indexes, quotation budgets, all 12 view-rendering paths, quiz correct/incorrect paths, context/spelling/listening flow, review scheduling, bookmarks, expression quizzes and backup/restore, ten-word unit scope, 12-unit path pagination, real-activity streaks, redesigned home markup, muted audio fallback, sentence saving/deduplication, usage quizzes and RTL word details. Verification used a DOM simulation; live browser visual QA, sound effects, speech and microphone operation were not available in the authoring environment and should be checked on your device.

## Rights

Original application code and original learning contributions use the accompanying MIT licence. Third-party dictionary content uses the WordNet licence included in `WORDNET_LICENSE.txt` and `meta.json`. Imported bank content retains its original rights; no licence was supplied in the attachment, so the MIT licence does not extend to it. Publisher excerpts remain subject to their respective rights. This project is not affiliated with the publishers or the reviewed learning platforms.
