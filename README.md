<div align="center">

# 🕉️ Sanatan Dharma — Sacred Texts & Divine Wisdom

**A complete, single-file interactive encyclopedia of Hinduism.**
Vedic scriptures · AI Guru · Live Panchang · Divine Family Tree · Mandala Creator · and more.

[![Made with Love](https://img.shields.io/badge/Made%20with-❤️%20%26%20Devotion-saffron?style=flat-square)](.)
[![Single File](https://img.shields.io/badge/Architecture-Single%20HTML%20File-gold?style=flat-square)](.)
[![No Backend](https://img.shields.io/badge/Backend-None%20Required-green?style=flat-square)](.)
[![GitHub Pages Ready](https://img.shields.io/badge/GitHub%20Pages-Ready-blue?style=flat-square)](.)

</div>

---

## 📋 Table of Contents

- [Official Website](#-official-website)
- [Overview](#-overview)
- [Repository Structure](#-repository-structure)
- [Deploying to GitHub Pages](#-deploying-to-github-pages)
- [Running Locally](#-running-locally)
- [Feature Guide](#-feature-guide)
  - [Sacred Texts Library](#-sacred-texts-library)
  - [Gods & Goddesses](#-gods--goddesses)
  - [Pillars of Philosophy](#-pillars-of-philosophy)
  - [Hindu Calendar & Festivals](#-hindu-calendar--festivals)
  - [Divine Family Tree](#-divine-family-tree)
  - [Mandala Creator](#-mandala-creator)
  - [Myths & Misconceptions](#-myths--misconceptions)
  - [Wisdom Podcasts](#-wisdom-podcasts)
  - [AI Guru — Dharma Guru Bot](#-ai-guru--dharma-guru-bot)
- [AI Guru — Full Setup Guide](#-ai-guru--full-setup-guide)
  - [Getting an API Key](#getting-an-api-key)
  - [Choosing a Model](#choosing-a-model)
  - [How the AI Actually Works — The 3-Layer System](#how-the-ai-actually-works--the-3-layer-system)
  - [Sacred Texts RAG — Indexing Guide](#sacred-texts-rag--indexing-guide)
- [Adding or Replacing PDF Books](#-adding-or-replacing-pdf-books)
- [Customisation Tips](#-customisation-tips)
- [Frequently Asked Questions](#-frequently-asked-questions)

---

## 🔗 Official Website

[Sanatana-Srota Official Website](https://shukdevtroy.github.io/Spotigrate-App/)

## 🌟 Overview

This project is a **zero-backend, single HTML file** that delivers a full Sanatan Dharma knowledge portal. Everything — styling, logic, animations, the AI chatbot, the calendar engine, the family tree, the mandala painter — lives inside `new_edition.html`. The only things fetched at runtime are Google Fonts, Font Awesome icons, PDF.js (for reading scripture PDFs), and the AI API calls you configure yourself.

**Key highlights:**

- Read and download all major Hindu scriptures as PDF directly in the browser
- A live AI Guru powered by your choice of LLM (Groq, OpenRouter, or HuggingFace)
- RAG (Retrieval-Augmented Generation): the AI answers questions by actually reading the scripture PDFs you index
- A real Vedic Panchang (Hindu calendar) calculated from astronomical formulas — not hardcoded
- Upcoming festival countdown with accurate lunar tithi calculations
- An interactive Divine Family Tree covering 35+ deities and avatars
- A meditative Mandala Creator with three sacred patterns and full colour control
- A scrolling ticker of Vedic shlokas and wisdom quotes
- A curated collection of Hindu wisdom videos (Indian teachers + Western perspectives)
- 9 common misconceptions about Sanatan Dharma — debunked with scriptural sources

---

## 📁 Repository Structure

Your repository should look exactly like this:

```
your-repo/
│
├── new_edition.html                        ← The entire website (open this)
│
├── Rig Veda.pdf
├── Sam Veda.pdf
├── Yajur Veda.pdf
├── Atharva Veda.pdf
├── Upanishads.pdf
├── Bhagavad-gita-As-It-Is.pdf
├── Ramayana.pdf
├── Mahabharata (Unabridged in English).pdf
├── Puranas.pdf
├── Hanuman_Chalisa_in_English.pdf
│
└── README.md                               ← This file
```

> **Important:** The PDF filenames must match exactly as listed above, including spaces and capitalisation. The HTML references these filenames directly.

---

## 🚀 Deploying to GitHub Pages

1. Push all files (the HTML + all PDFs) to a GitHub repository.
2. Go to your repository → **Settings** → **Pages**.
3. Under *Source*, select **Deploy from a branch** → choose `main` (or `master`) → folder `/root`.
4. Click **Save**. GitHub will give you a URL like `https://yourusername.github.io/your-repo/`.
5. Open that URL and append `/new_edition.html` — e.g. `https://yourusername.github.io/your-repo/new_edition.html`.

Once live on GitHub Pages, **all PDF indexing works automatically** — no file picker needed. The browser can fetch PDFs freely over HTTP.

---

## 💻 Running Locally

Open `new_edition.html` directly in your browser by double-clicking it. Everything works except one thing: **browsers block local file reads for security reasons**, so the "Index for AI" button cannot auto-load PDFs on `file://`.

**Workaround for local PDF indexing:**

1. Click **🧠 Index for AI** on any book card (or **＋ Index PDF** in the chat).
2. A notification appears: *"Local mode — select [filename] from your SANATANS folder"*, and a file picker opens.
3. Navigate to your folder, click the PDF, and it indexes instantly under the correct book title.

This is a browser limitation — not a bug. On GitHub Pages this step is skipped entirely.

> **Tip for power users:** If you want fully automatic local indexing without file pickers, serve the folder with a local server:
> ```bash
> # Python
> python -m http.server 8000
> # Then open: http://localhost:8000/new_edition.html
> ```

---

## 🗺️ Feature Guide

### 📚 Sacred Texts Library

**Location:** `#texts` — first section after the hero

The library contains 10 sacred scriptures displayed as glowing book cards:

| Book | Category |
|------|----------|
| Rig Veda | Veda |
| Sam Veda | Veda |
| Yajur Veda | Veda |
| Atharva Veda | Veda |
| Upanishads | Vedanta |
| Bhagavad Gita As It Is | Smriti |
| Ramayana | Itihasa |
| Mahabharata (Unabridged) | Itihasa |
| Puranas | Purana |
| Hanuman Chalisa | Stotra |

**Each card has three buttons:**

- **📖 Read** — Opens the PDF in a full-screen in-browser viewer with a "New Tab" option.
- **⬇ Download PDF** — Triggers a direct download of the PDF file.
- **🧠 Index for AI** — Processes the PDF through the RAG engine so the AI Guru can quote it when answering your questions. See the [RAG section](#sacred-texts-rag) for full details.

---

### 🙏 Gods & Goddesses

**Location:** `#deities` — below the sacred texts

Displays 12 deity cards. **Click any card** to open a popup showing:
- The deity's image fetched live from Wikipedia
- Their name and divine epithet
- A fallback emoji icon if the image fails to load

Deities included: Lord Shiva, Lord Vishnu, Brahma, Goddess Lakshmi, Goddess Durga, Goddess Saraswati, Lord Ganesha, Lord Krishna, Lord Rama, Lord Surya, Lord Kartikeya, Hanuman Ji.

Press **Esc** or click outside the popup to close it.

---

### 🔵 Pillars of Philosophy

**Location:** `#philosophy` — below the deities, after the scrolling quote ticker

Six foundational concepts of Sanatan Dharma explained in glowing cards:

**Dharma · Karma · Samsara · Moksha · Ahimsa · Bhakti**

The quote ticker above this section scrolls Vedic shlokas and wisdom quotes continuously. It runs on pure CSS animation — no interaction needed.

---

### 📅 Hindu Calendar & Festivals

**Location:** `#calendar-section`

**Left panel — Live Panchang:**
The Panchang is calculated in real-time using astronomical formulas (Julian Day Numbers, lunar elongation). It shows:

| Field | Meaning |
|-------|---------|
| **Tithi** | Lunar day (e.g. Ekadashi, Purnima, Amavasya) |
| **Nakshatra** | The lunar mansion the Moon currently occupies |
| **Paksha** | Shukla (waxing) or Krishna (waning) fortnight |
| **Vara** | Day of the week in Sanskrit |
| **Masa** | Current lunar month (e.g. Chaitra, Vaishakha) |
| **Samvat** | Vikram Samvat year |

The Panchang refreshes automatically every 10 minutes in case the tithi changes mid-day.

Below the Panchang card is a **countdown timer** to the next major upcoming festival, updated live.

**Right panel — Festival Calendar:**
Lists all major Hindu festivals for the year with accurate dates calculated from tithi formulas (not hardcoded). Includes: Makar Sankranti, Maha Shivratri, Holi, Ram Navami, Hanuman Jayanti, Akshaya Tritiya, Guru Purnima, Raksha Bandhan, Janmashtami, Ganesh Chaturthi, Navratri, Dussehra, Karva Chauth, Diwali, and more. The **next upcoming festival** is highlighted.

---

### 🌳 Divine Family Tree

**Location:** `#family-tree`

An interactive SVG graph of 35+ deities, avatars, and sages showing their cosmic relationships. Covers:

- The Trimurti: Brahma, Vishnu, Shiva
- The Dashavatara (10 Avatars of Vishnu): Matsya, Kurma, Varaha, Narasimha, Vamana, Parashurama, Rama, Krishna, Balarama, Kalki
- Consorts: Saraswati, Lakshmi, Sati Devi, Rukmini, Radha Rani, Goddess Sita
- Sages & Progenitors: Narada Muni, Daksha Prajapati, Maharishi Marichi, Kashyapa Rishi, Aditi
- Others: Indra, Lord Surya, Pradyumna, Aniruddha, Hanuman Ji, Lava & Kusha

**Controls:**

| Action | How |
|--------|-----|
| Pan / drag | Click and drag on the background |
| Zoom | Mouse wheel / trackpad scroll |
| View deity info | Click any deity node |
| Close info panel | Click the background |
| Reset view | The view auto-fits on load |
| Download | Click **⬇ Download** — saves as a standalone HTML file |

---

### 🎨 Mandala Creator

**Location:** `#mandala-tool`

A meditative drawing tool. Choose a sacred pattern, pick colours, and paint by clicking or dragging on the canvas.

**Pattern types:**

- 🌸 **Lotus** — Concentric petal rings radiating from the centre
- ☸ **Chakra** — Wheel geometry with spokes and rings
- 🔺 **Sri Yantra** — Nested triangles in the sacred yantra formation

**Colour palette:** Click any colour swatch to select it. Use the **custom colour picker** (🎨 icon) for any colour in the spectrum.

**Action buttons:**

| Button | Function |
|--------|----------|
| **↩ Undo** | Removes the last stroke |
| **🗑 Clear** | Wipes the canvas clean |
| **⬇ Save** | Downloads your mandala as a PNG image |

All strokes respect the pattern's symmetry — whatever you draw on one axis is mirrored across all others.

---

### 📖 Myths & Misconceptions

**Location:** `#misconceptions`

Nine common misconceptions about Sanatan Dharma, each presented as a card with the myth clearly stated and the Vedic truth explained with scriptural citations:

1. "Hindus worship cows as God" — *Rigveda 6.28*
2. "Hinduism has 330 million Gods / is polytheistic" — *Rigveda 1.164.46*
3. "The caste system is a core Vedic teaching" — *Bhagavad Gita 4.13*
4. "Hindus are fatalistic / believe in predestination" — *Bhagavad Gita 3.19*
5. "Hinduism oppresses women" — *Rigveda Devi Suktam*
6. "Hinduism is only for Indians / a regional religion" — *Maha Upanishad 6.71*
7. "All Hindus must be vegetarian" — *Mahabharata Anushasana Parva*
8. "The Ramayana and Mahabharata are just myths" — *Valmiki Ramayana*
9. "Idol worship is superstition" — *Bhagavad Gita 12.2–5*

---

### 🎙 Wisdom Podcasts

**Location:** `#podcasts`

A curated grid of Hindu wisdom videos, split into two tabs:

**🇮🇳 Indian Teachers** — Sadhguru, Gaur Gopal Das, Gurudev Sri Sri Ravi Shankar, and others explaining concepts like Shiva, the Bhagavad Gita, consciousness, and life after death.

**🌍 Western Perspectives** — Western scholars, speakers, and thinkers engaging with Hindu philosophy, including Devdutt Pattanaik's TED Talk and cross-cultural comparisons.

Click any card to open the video on YouTube. Switch tabs with the **Indian / Western** buttons at the top of the section.

---

### 🤖 AI Guru — Dharma Guru Bot

**Location:** `#chatbot-section` — fixed **Chat** button in the navbar also jumps here

The AI Guru is a conversational assistant pre-instructed as *Dharma Guru* — an expert in the Vedas, Upanishads, Bhagavad Gita, Puranas, and Hindu mythology. It can answer questions, explain concepts, discuss stories, and — when RAG is enabled — quote directly from the actual scripture PDFs.

**Quick-start chips** (click to send instantly):
- What is the meaning of OM?
- Explain the Bhagavad Gita's core teachings
- Who are the Ashta Dikpalakas?
- What are the 4 Vedas?
- Tell me about Lord Hanuman
- What is Moksha?
- Describe the Mahabharata war

---

## 🔑 AI Guru — Full Setup Guide

The AI Guru requires an API key from one of three providers. **All providers have free tiers** — no payment needed to get started.

### Getting an API Key

**Option 1 — Groq (Recommended · Fastest responses)**
1. Go to [console.groq.com](https://console.groq.com) and sign up for free.
2. Navigate to **API Keys** → **Create API Key**.
3. Copy the key — it starts with `gsk_`.
4. In the website, scroll to the AI Guru section → paste into **Groq API Key** field → click **Save Groq**.

**Option 2 — OpenRouter (Most model variety · Fully free options)**
1. Go to [openrouter.ai](https://openrouter.ai) and sign up.
2. Go to **Keys** → **Create Key**.
3. Copy the key — it starts with `sk-or-`.
4. Paste into **OpenRouter API Key** field → click **Save OpenRouter**.

**Option 3 — HuggingFace (Good for experimentation)**
1. Go to [huggingface.co](https://huggingface.co) and sign up.
2. Go to **Settings** → **Access Tokens** → **New Token** (read access is enough).
3. Copy the token — it starts with `hf_`.
4. Paste into **HuggingFace Token** field → click **Save HF**.

> Your API keys are saved to your **browser's localStorage** — they never leave your device and are never sent anywhere except directly to the API provider.

---

### Choosing a Model

Use the **Model** dropdown in the chat header to switch models at any time:

| Model | Provider | Best for |
|-------|----------|----------|
| **LLaMA 3.3 70B** | Groq | Best quality + fast — recommended default |
| LLaMA 3.1 8B Instant | Groq | Ultra-fast, lighter answers |
| Gemma2 9B | Groq | Good for concise factual answers |
| Mixtral 8x7B | Groq | Well-rounded, strong reasoning |
| LLaMA 3.3 70B Free | OpenRouter | Free tier, same quality as Groq LLaMA |
| Mistral 7B Free | OpenRouter | Lightweight free option |
| Gemma 3 27B Free | OpenRouter | Google's latest, free |
| DeepSeek R1 Free | OpenRouter | Strong reasoning model, free |
| Qwen3 235B Free | OpenRouter | Largest free model available |
| Mixtral 8x7B | HuggingFace | Classic, widely supported |
| Zephyr 7B | HuggingFace | Lightweight, good instruction following |

---

### How the AI Actually Works — The 3-Layer System

Every time you send a message, the code builds a packet of information and sends it to the AI. This packet is assembled in **3 layers**, and all three providers (Groq, OpenRouter, HuggingFace) receive the exact same packet.

---

**Layer 1 — System Prompt (always present, no toggle)**

This is the permanent base personality of Dharma Guru. It is always included regardless of any settings. It tells the model who it is, how to speak, what it knows, and how to answer — the full Sanatani AI persona, tone, and rules. No toggle can remove this layer.

---

**Layer 2 — Web Search (🔍 toggle)**

When **Web Search is ON** (default):
- Before calling the AI, the code searches DuckDuckGo for your question + *"Hinduism Sanatan Dharma"*
- It pulls back a short abstract and up to 4 source links
- This is appended to the system prompt as `[Web Search Context]: ...`
- The AI now has current/external information to draw from alongside its training knowledge

When **Web Search is OFF**:
- This step is skipped entirely — no web lookup happens
- Responses are faster since there's no network call before the AI call
- The AI answers purely from its training knowledge (and scripture passages if RAG is on)

---

**Layer 3 — Sacred Texts RAG (📚 toggle + indexed PDFs)**

When **RAG is ON and you have PDFs indexed**:
- The code searches your indexed scripture chunks using TF-IDF similarity matching against your question
- It picks the **4 most relevant passages** from all your indexed books
- Those passages are appended to the system prompt as `[Sacred Text Passages — use these as primary reference, cite the source]: ...`
- The AI now has the actual Vedic text in front of it and can quote verse and chapter directly

When **RAG is OFF or no PDFs are indexed**:
- This step is skipped
- No scripture passages are added to the prompt

---

**What gets sent to the AI (final assembled packet)**

```
┌─────────────────────────────────────────────────┐
│  SYSTEM MESSAGE                                 │
│  = Dharma Guru persona (always)                 │
│  + [Web Search Context] (if search ON)          │
│  + [Sacred Text Passages] (if RAG ON + indexed) │
├─────────────────────────────────────────────────┤
│  Last 10 messages of your conversation          │
├─────────────────────────────────────────────────┤
│  Your current question                          │
└─────────────────────────────────────────────────┘
```

This identical packet is sent to whichever provider you have selected — Groq and OpenRouter receive it as a native `messages` array with a proper `system` role, while HuggingFace receives it formatted as an `[INST]...[/INST]` instruction string (which is the format those models understand).

---

**The 4 possible combinations**

| Web Search | RAG | What the AI knows | Best used when |
|---|---|---|---|
| ✅ ON | ✅ ON | Persona + live web + actual scripture text | Deep, cited, up-to-date answers |
| ✅ ON | ❌ OFF | Persona + live web only | General questions, current events |
| ❌ OFF | ✅ ON | Persona + scripture passages only | Pure Vedic answers from the texts |
| ❌ OFF | ❌ OFF | Persona + model training only | Fastest responses, no extra context |

---

### Sacred Texts RAG — Indexing Guide

RAG (Retrieval-Augmented Generation) is what allows the AI to answer by **reading the actual scripture PDFs** rather than relying on training data alone. You need to index a PDF at least once per browser session before RAG can use it.

**Enabling RAG:**
1. Toggle **📚 Sacred Texts RAG** ON in the chat model bar. The RAG status bar appears below.
2. Click **🧠 Index for AI** on any book card, or click **＋ Index PDF** in the RAG status bar.

**How indexing works on GitHub Pages (fully automatic):**
- The PDF is fetched directly from the repo by relative path
- PDF.js extracts all text page by page and splits it into ~400-word chunks with 80-word overlaps
- TF-IDF vectors are computed for every chunk and stored in browser memory
- A progress bar shows extraction progress
- On completion: *"📚 'Bhagavad Gita' indexed — 842 chunks ready"*

**How indexing works locally on your PC (one extra click):**
- Browsers block local file reads on `file://` for security — this cannot be bypassed
- A file picker opens automatically with a prompt saying which file to select
- Navigate to your `SANATANS` folder, click the PDF, and it indexes under the correct book title
- This is a one-time click per session — once indexed it works for the rest of the session

**Indexing multiple books:**
Index as many books as you want. Each appears as a pill tag in the RAG status bar. Click **✕** on any pill to remove it from the index.

**Upload Your Own PDF:**
In the RAG modal (**＋ Index PDF**), the **Upload Your Own PDF** section lets you index any PDF not in the default library — a commentary, personal scripture, translation, etc. The title is taken from the filename.

> **Note:** The RAG index lives in browser memory only and is cleared when you close or refresh the tab. You will need to re-index at the start of each session.

---

## 📄 Adding or Replacing PDF Books

To add a new scripture to the library, edit the `BOOKS` array near line 4042 in `new_edition.html`:

```javascript
{
  title: "Yoga Sutras of Patanjali",
  file: "Yoga Sutras.pdf",           // must match the actual filename in your repo
  symbol: "🧘",
  category: "Darshana",
  bg: "linear-gradient(135deg,#4B0082,#D4A017)",
  desc: "The 196 aphorisms of Patanjali — the foundational text of classical Yoga philosophy."
},
```

Then place `Yoga Sutras.pdf` in the same folder as `new_edition.html` and push to GitHub.

To **replace** an existing PDF (e.g. a better translation), simply replace the file in your repo with the same filename — no code changes needed.

---

## 🎨 Customisation Tips

**Change the sitewide accent colours** — edit the CSS variables at the very top of the `<style>` block:
```css
:root {
  --saffron: #FF6B00;      /* primary orange */
  --gold: #D4A017;         /* gold accents */
  --crimson: #8B0000;      /* deep red */
  --bg-dark: #0A0400;      /* page background */
}
```

**Add a new deity card** — find the `.deities-grid` div and add:
```html
<div class="deity-card reveal">
  <span class="deity-icon">🌙</span>
  <div class="deity-name">Lord Chandra</div>
  <div class="deity-epithet">The Moon God</div>
  <div class="deity-hint"><span class="deity-hint-dot"></span>Click to view</div>
</div>
```
Then add the deity's Wikipedia page title to the `DEITY_WIKI` object in the script to enable live image fetching.

**Add a quote to the ticker** — find the `TICKER_QUOTES` array and add:
```javascript
{ text: "Aham Brahmasmi — I am Brahman.", src: "Brihadaranyaka Upanishad 1.4.10" },
```

**Change the AI system prompt** — find `const SYSTEM_PROMPT` (~line 4345) to adjust the AI's persona, tone, or areas of focus.

---

## ❓ Frequently Asked Questions

**Q: Does this work without an internet connection?**
A: Partially. The page structure, Panchang, Family Tree, Mandala Creator, Myths & Misconceptions, and Philosophy sections all work offline. The AI Guru, web search, deity popup images (Wikipedia), fonts, and PDF.js require internet.

**Q: Are my API keys safe?**
A: Yes. Keys are stored in your browser's `localStorage` and are sent only directly to the respective API provider (Groq, OpenRouter, or HuggingFace). The website itself has no server — there is nothing to leak your keys to.

**Q: The AI says it needs an API key — which provider should I use?**
A: **Groq** with LLaMA 3.3 70B is the recommended starting point. It's free, fast, and gives the best quality answers for this use case. Sign up at [console.groq.com](https://console.groq.com).

**Q: Why does indexing take a while for large PDFs?**
A: PDF.js extracts text page by page. A large text like the Mahabharata (1000+ pages) may take 30–60 seconds to fully index. The progress bar shows how far along it is. Once complete, all subsequent queries use the indexed memory instantly.

**Q: The indexed text disappears after I close the tab. Is that normal?**
A: Yes — the RAG index lives in JavaScript memory and is not persisted. This is intentional to keep the project serverless and private. You'll need to re-index after each browser session.

**Q: Can I host this on Netlify / Vercel / Cloudflare Pages instead of GitHub Pages?**
A: Absolutely. Any static file host works. Just upload `new_edition.html` and all PDFs to the same directory.

**Q: The Panchang shows a slightly different tithi than my local calendar. Why?**
A: The Panchang is calculated from astronomical formulas using UTC time. Regional Hindu calendars can vary by ±1 tithi depending on the local sunrise time used and the specific regional tradition (Amanta vs Purnimanta months). For most purposes the calculation is accurate to within one tithi.

**Q: How do I update the festival list for a new year?**
A: You don't need to. The festivals are calculated dynamically from tithi formulas each time the page loads, so they automatically show correct dates for whatever the current year is.

---

<div align="center">

---

*ॐ सर्वे भवन्तु सुखिनः। सर्वे सन्तु निरामयाः।*
*May all beings be happy. May all beings be free from illness.*

**जय सनातन धर्म 🙏**

</div>
