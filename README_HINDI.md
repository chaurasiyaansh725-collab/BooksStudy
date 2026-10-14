# BooksStudy.com — मोबाइल-फ्रेंडली Android ऐप स्टार्टर

यह प्रोजेक्ट एक **installable web app (PWA)** है, जिसे Android Chrome से Home Screen पर जोड़ा जा सकता है। इसमें BooksStudy का UI, विषय चुनना, सवाल टाइप करना, फोटो जोड़ना और AI tutor interface शामिल है।

## महत्वपूर्ण बात
अभी यह ऐप अपने-आप इंटरनेट पर प्रकाशित नहीं है। लाइव AI उत्तर पाने के लिए इस Node.js सर्वर को HTTPS hosting पर deploy करना और hosting के Environment Variables में `OPENAI_API_KEY` सेट करना ज़रूरी है। API key को `public/` फाइलों में कभी न डालें। OpenAI API usage के लिए बिलिंग/उपलब्धता की ज़रूरत हो सकती है।

## फ़ाइलें
- `public/index.html` — ऐप का इंटरफ़ेस
- `public/manifest.json` — Android install metadata
- `public/sw.js` — सीमित offline shell cache
- `server.js` — सुरक्षित server-side AI API route
- `package.json` — Node dependencies

## Deploy (किसी Node.js hosting पर)
1. इस ZIP को extract करें या project को Git repository में डालें।
2. Node.js hosting चुनें जो web service चलाती हो और environment variables सपोर्ट करती हो।
3. Build command: `npm install`
4. Start command: `npm start`
5. Environment variable जोड़ें:
   - `OPENAI_API_KEY` = आपकी निजी OpenAI API key
   - वैकल्पिक: `OPENAI_MODEL` = कोई ऐसा मॉडल जो आपके API खाते में उपलब्ध हो और Responses API व image input सपोर्ट करता हो
6. Hosting द्वारा दिया गया HTTPS URL खोलकर जाँचें।
7. Android पर Chrome में URL खोलें → Chrome menu (⋮) → **Add to Home screen** या **Install app**.

## सुरक्षा
- API key सिर्फ hosting के server-side environment variable में रखें।
- इसे HTML, JavaScript, GitHub public repository या स्क्रीनशॉट में न डालें।
- Production में rate limiting, authentication/abuse protection, usage limits और privacy notice जोड़ना उचित है।
- फोटो सर्वर तक AI processing के लिए जाती है; केवल वही फोटो भेजें जिन्हें साझा करना ठीक हो।

## वर्तमान सीमाएँ
- यह पूरा महाराष्ट्र बोर्ड प्रश्न बैंक नहीं है; अभी कोई आधिकारिक किताब/सभी अभ्यास प्रश्न शामिल नहीं हैं।
- उत्तर AI द्वारा बनाए जाते हैं, इसलिए किताब/शिक्षक से सत्यापित करें।
- यह PWA है, native APK नहीं। Home Screen पर ऐप जैसा खुलेगा, लेकिन इसे Play Store पर प्रकाशित नहीं किया गया है।
- AI route तब तक जवाब नहीं देगा जब तक backend deploy न हो और API key सुरक्षित रूप से सेट न हो।
