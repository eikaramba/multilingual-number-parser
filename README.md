# 🌍 i18n-number-parser

A powerful multilingual library for converting written numbers to their numeric equivalents across multiple languages. Perfect for parsing voice assistant outputs, natural language processing, and internationalization needs.

## 🚀 Why Use This Library?

### Voice Assistant Integration
Voice assistants often return spoken numbers as text. This library seamlessly converts them back to numbers:
```javascript
// Voice assistant says: "Set a timer for twenty-five minutes"
wordsToNumbers("Set a timer for twenty-five minutes", { language: 'en-us' })
// → "Set a timer for 25 minutes"
```

### Natural Language Processing
Process user input containing written numbers in multiple languages:
```javascript
// German: "Ich möchte fünfundzwanzig Äpfel kaufen"
wordsToNumbers("Ich möchte fünfundzwanzig Äpfel kaufen", { language: 'de-de' })
// → "Ich möchte 25 Äpfel kaufen"
```

### Internationalization
Support users worldwide with consistent number parsing across languages.

## 📦 Installation

```bash
npm install i18n-number-parser
# or
pnpm install i18n-number-parser
# or
yarn add i18n-number-parser
```

## 🌐 Supported Languages

- **English** (`en-us`) - "twenty-five", "one hundred", "five point seven"
- **German** (`de-de`) - "fünfundzwanzig", "einhundert", "fünf Komma sieben"
- **Dutch** (`nl-nl`) - "vijfentwintig", "één honderd", "vijf komma zeven"
- **Portuguese** (`pt-br`) - "vinte e cinco", "cem", "cinco vírgula sete"

## 🔧 Usage

### Basic Usage

```javascript
import wordsToNumbers from 'i18n-number-parser';
import { Languages } from 'i18n-number-parser';

// English
wordsToNumbers("twenty-five", { language: Languages['en-us'] });
// → 25

// German
wordsToNumbers("fünfundzwanzig", { language: Languages['de-de'] });
// → 25

// Dutch
wordsToNumbers("vijfentwintig", { language: Languages['nl-nl'] });
// → 25

// Portuguese
wordsToNumbers("vinte e cinco", { language: Languages['pt-br'] });
// → 25
```

### Advanced Examples

#### Large Numbers
```javascript
// English
wordsToNumbers("two million six hundred twenty two thousand three hundred eighty eight", 
  { language: Languages['en-us'] });
// → 2622388

// German
wordsToNumbers("zwei Millionen sechshundertzweiundzwanzigtausenddreihundertachtundachtzig", 
  { language: Languages['de-de'] });
// → 2622388
```

#### Decimal Numbers
```javascript
// English
wordsToNumbers("five point twenty one", { language: Languages['en-us'] });
// → 5.21

// German - individual digits after decimal
wordsToNumbers("fünf Komma zwei eins", { language: Languages['de-de'] });
// → 5.21

// Portuguese - compound numbers after decimal
wordsToNumbers("cinco vírgula vinte e um", { language: Languages['pt-br'] });
// → 5.21
```

#### Mixed Text
```javascript
// Replace numbers in sentences
wordsToNumbers("I have twenty-five apples and thirty oranges", 
  { language: Languages['en-us'] });
// → "I have 25 apples and 30 oranges"

// German
wordsToNumbers("Ich habe fünfundzwanzig Äpfel und dreißig Orangen", 
  { language: Languages['de-de'] });
// → "Ich habe 25 Äpfel und 30 Orangen"
```

#### Ordinal Numbers
```javascript
// English
wordsToNumbers("The twenty-second of May", { language: Languages['en-us'] });
// → "The 22 of May"

// German
wordsToNumbers("Der zweiundzwanzigste Mai", { language: Languages['de-de'] });
// → "Der 22 Mai"
```

## ⚙️ Options

```typescript
interface Options {
  language: Languages;     // Required: Language to parse
  numbersOnly?: boolean;   // Return array of numbers only
  oneNumber?: boolean;     // Concatenate all numbers into one
  useSuffix?: boolean;     // Handle suffixes (experimental)
  debug?: boolean;         // Enable debug logging
}
```

### Options Examples

#### Numbers Only
```javascript
wordsToNumbers("I have twenty-five apples and thirty oranges", {
  language: Languages['en-us'],
  numbersOnly: true
});
// → [25, 30]
```

#### One Number
```javascript
wordsToNumbers("nineteen ninety eight", {
  language: Languages['en-us'],
  oneNumber: true
});
// → 1998
```

## 🎯 Use Cases

### 1. Voice Assistant Integration
```javascript
// Alexa/Google Assistant output processing
const voiceOutput = "Set timer for twenty five minutes";
const processed = wordsToNumbers(voiceOutput, { language: Languages['en-us'] });
// Use processed text for timer: "Set timer for 25 minutes"
```

### 2. Form Input Processing
```javascript
// User types numbers as words
const userInput = "I want to order twenty-five items";
const normalized = wordsToNumbers(userInput, { language: Languages['en-us'] });
// Store normalized: "I want to order 25 items"
```

### 3. Document Processing
```javascript
// Convert written numbers in documents
const document = "The report shows twenty-three percent growth";
const processed = wordsToNumbers(document, { language: Languages['en-us'] });
// → "The report shows 23 percent growth"
```

### 4. Multilingual Chat Bots
```javascript
// Handle different languages dynamically
function processMessage(message, userLanguage) {
  return wordsToNumbers(message, { language: userLanguage });
}

processMessage("Ich brauche fünf Tickets", Languages['de-de']);
// → "Ich brauche 5 Tickets"
```

## 🔍 Language-Specific Features

### German
- Compound numbers: `"einundzwanzig"` → `21`
- Complex compounds: `"zweihundertdreiundzwanzig"` → `223`
- Decimal handling: `"fünf Komma zwei eins"` → `5.21`

### Dutch
- Reversed order: `"vijfentwintig"` (five-and-twenty) → `25`
- Special characters: `"drieëndertig"` → `33`

### Portuguese
- Compound decimals: `"cinco vírgula quinhentos e vinte e um"` → `5.521`
- Gender variations: `"uma"`, `"dois"/"duas"`

### English
- Hyphenated numbers: `"twenty-five"` → `25`
- Point decimals: `"five point two one"` → `5.21`

## 🧪 Testing

The library includes comprehensive test suites for all supported languages:

```bash
pnpm test
```

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request. The library is designed to be easily extensible for additional languages.

## 📄 License

MIT License - see LICENSE file for details.

## 🙏 Acknowledgments

Originally based on [words-to-numbers](https://github.com/finnfiddle/words-to-numbers) and [multilingual-number-parser](https://github.com/metamaze/multilingual-number-parser), with significant improvements including:

- Fixed test suite and compilation issues
- Added comprehensive German language support
- Improved decimal number handling across languages
- Enhanced language-specific parsing logic
- Better error handling and edge cases

## 📊 Performance

- Lightweight: < 10KB minified
- Fast parsing with optimized algorithms
- Memory efficient with minimal dependencies
- TypeScript support included
