# First Aid Dataset

A comprehensive, structured JSON-based dataset providing offline first aid guidance in Arabic for mobile and desktop applications.

## Table of Contents

- [Overview](#overview)
- [Dataset Structure](#dataset-structure)
- [Data Schema](#data-schema)
- [Example JSON](#example-json)
- [Search System](#search-system)
- [Media Handling](#media-handling)
- [Localization](#localization)
- [How to Extend](#how-to-extend)
- [Disclaimer](#disclaimer)
- [License](#license)

## Overview

This dataset provides structured first aid information designed specifically for offline applications serving Arabic-speaking users. The data is organized for fast lookup, intelligent matching, and seamless integration with chatbot systems and mobile interfaces.

**Key Features:**

- Production-ready JSON structure optimized for offline use
- Bilingual keyword support (Arabic and English) for flexible searching
- Severity levels to distinguish urgency (low, medium, high)
- Separate instructions for adults and children where applicable
- Media integration with images and video links
- Lightweight and scalable architecture

## Dataset Structure

```
first-aid-dataset/
├── assets/
│   └── images/                    # Medical images categorized by condition
│       ├── allergies_skin/
│       ├── burns/
│       ├── cpr/
│       ├── diabetes/
│       ├── digestive/
│       ├── emergency/
│       ├── environmental/
│       ├── eye_injury/
│       ├── general_illness/
│       ├── musculoskeletal/
│       ├── neurological/
│       ├── poisoning/
│       ├── respiratory/
│       ├── stings/
│       └── wounds_bleeding/
│
├── data/
│   ├── arabic/
│   │   ├── emergency_numbers/     # Emergency contact numbers for Arab countries
│   │   ├── first_aid_kit/         # First aid kit contents and preparation guide
│   │   └── first_aid_data/        # Main first aid cases and instructions
│   │
│   └── english/                   # (Planned for future localization)
│
├── LICENSE
├── README.md
└── assets/images/... (as detailed above)
```

### Folder Purposes

| Folder                           | Purpose                                                               |
| -------------------------------- | --------------------------------------------------------------------- |
| `assets/images/`                 | Visual guides organized by medical category, referenced in JSON cases |
| `data/arabic/emergency_numbers/` | Emergency contact numbers for each Arab country                       |
| `data/arabic/first_aid_kit/`     | Contents and setup instructions for first aid kits                    |
| `data/arabic/first_aid_data/`    | Main dataset containing all first aid cases and guidance              |
| `data/english/`                  | Reserved for English localization expansion                           |

## Data Schema

The `first_aid_data.json` file contains the core dataset with the following structure:

### Root Level

| Field          | Type   | Description                                                     |
| -------------- | ------ | --------------------------------------------------------------- |
| `version`      | String | Dataset version (e.g., "1.0.0")                                 |
| `last_updated` | String | Last update date in YYYY-MM-DD format                           |
| `language`     | String | Language code (e.g., "ar" for Arabic)                           |
| `schema`       | Object | Metadata about the schema, including severity level definitions |
| `topics`       | Array  | Array of first aid cases                                        |

### Topic Object

| Field                | Type    | Description                                                      |
| -------------------- | ------- | ---------------------------------------------------------------- |
| `id`                 | Integer | Unique identifier for the case                                   |
| `category`           | String  | Medical category (e.g., "emergency", "burns", "respiratory")     |
| `severity`           | Integer | 1 (Low), 2 (Medium), or 3 (High/Life-threatening)                |
| `title`              | String  | Case title in Arabic                                             |
| `keywords`           | Object  | Search keywords in Arabic (`ar`) and English (`en`)              |
| `adult_instructions` | Array   | Step-by-step instructions for adult patients                     |
| `adults_media`       | Object  | Images and video references for adult guidance                   |
| `has_child`          | Boolean | Indicates if different child instructions are available          |
| `child_instructions` | Array   | Step-by-step instructions for pediatric patients (if applicable) |
| `child_media`        | Object  | Images and video references for child guidance (if applicable)   |

### Media Object Structure

```json
{
  "video": "https://www.youtube.com/watch?v=VIDEO_ID",
  "images": [
    "assets/images/category/image_1.png",
    "assets/images/category/image_2.png"
  ]
}
```

## Example JSON

Here is a complete example of a first aid case (CPR):

```json
{
  "id": 1,
  "category": "emergency",
  "severity": 3,
  "title": "الإنعاش القلبي الرئوي (CPR)",
  "keywords": {
    "ar": ["CPR", "إنعاش قلبي رئوي", "توقف التنفس", "لا يتنفس", "توقف القلب"],
    "en": ["CPR", "cardiopulmonary resuscitation", "no pulse"]
  },
  "adult_instructions": [
    "Call emergency services immediately",
    "Place the person on a firm, flat surface",
    "Press on the center of the chest at 100-120 compressions per minute",
    "If untrained: continue chest compressions until help arrives",
    "If trained: perform 30 chest compressions followed by 2 rescue breaths",
    "Use an AED device if available",
    "Continue until emergency personnel arrives or breathing returns"
  ],
  "adults_media": {
    "video": "https://www.youtube.com/watch?v=VIDEO_ID",
    "images": [
      "assets/images/cpr/cpr_adults_1.png",
      "assets/images/cpr/cpr_adults_2.png"
    ]
  },
  "has_child": true,
  "child_instructions": [
    "For infants: Use two fingers to compress the center of chest",
    "For children: Use one or two hands depending on child size",
    "Compression rate: 100-120 per minute, depth 2 inches",
    "Follow same pattern: 30 compressions, 2 breaths",
    "Continue until emergency arrives or normal breathing returns"
  ],
  "child_media": {
    "video": "https://www.youtube.com/watch?v=CHILD_VIDEO_ID",
    "images": [
      "assets/images/cpr/cpr_child_1.png",
      "assets/images/cpr/cpr_child_2.png"
    ]
  }
}
```

## Search System

The keyword system enables flexible, user-friendly searching in both Arabic and English:

- **Bilingual Keywords**: Each case includes keywords in Arabic (`ar`) and English (`en`) for multilingual support
- **Symptom Matching**: Keywords map user symptoms to appropriate first aid guidance (e.g., searching "لا يتنفس" or "not breathing" returns CPR case)
- **Search Implementation**: Applications should:
  1. Convert user input to lowercase
  2. Search across both Arabic and English keyword arrays
  3. Return matching cases ranked by relevance
  4. Consider severity levels in sorting results

**Example Search Flow:**

```
User input: "burns" (English) or "حروق" (Arabic)
→ Match against keyword arrays
→ Return all burn-related cases
→ Sort by severity (high → medium → low)
```

## Media Handling

### Image Files

- Images are stored in categorized folders under `assets/images/`
- Each case references images via relative file paths
- Image paths follow the pattern: `assets/images/{category}/{specific_image}.png`
- Applications should load images relative to the dataset root directory

### Video Content

- Videos are hosted on YouTube for accessibility and offline capability
- Each case includes a YouTube URL in the `video` field
- Videos are provided as supplementary educational material
- Applications can extract video IDs from URLs for thumbnail generation or embedded playback

### File References

```json
"adults_media": {
  "video": "https://www.youtube.com/watch?v=r2FjOmHtPpQ",
  "images": ["assets/images/cpr/cpr_adults_1.png"]
}
```

## Localization

### Current State

- **Arabic**: Fully developed with complete first aid guidance, keywords, and cultural relevance
- **English**: Folder structure prepared for future expansion

### Future English Support

The dataset is designed to support English localization without restructuring:

- Create parallel JSON files in `data/english/`
- Maintain identical structure and `id` mappings
- Applications can load language variants based on user preferences

### Adding a New Language

1. Create a new folder: `data/{language_code}/`
2. Mirror the Arabic structure (emergency_numbers, first_aid_kit, first_aid_data)
3. Translate all content while maintaining:
   - Identical `id` values for cross-referencing
   - Same category names for consistency
   - Severity levels unchanged
4. Update application language switching logic to load the appropriate version

## How to Extend

### Adding a New First Aid Case

1. **Open** `data/arabic/first_aid_data/first_aid_data.json`

2. **Determine the next ID** by checking the highest existing ID

3. **Add a new object to the `topics` array:**

   ```json
   {
     "id": 23,
     "category": "burns",
     "severity": 2,
     "title": "حروق الدرجة الثانية",
     "keywords": {
       "ar": ["حروق", "الجلد المحروق", "فقاعات"],
       "en": ["burns", "second degree", "blisters"]
     },
     "adult_instructions": [
       "Step 1: Cool the burn with water for 15-20 minutes",
       "Step 2: Remove tight clothing or jewelry",
       "Step 3: Cover with sterile gauze",
       "Step 4: Seek medical attention"
     ],
     "adults_media": {
       "video": "https://www.youtube.com/watch?v=VIDEO_ID",
       "images": ["assets/images/burns/burn_treatment.png"]
     },
     "has_child": true,
     "child_instructions": [...],
     "child_media": {...}
   }
   ```

4. **Add corresponding images** to the appropriate category folder in `assets/images/`

5. **Update** the `last_updated` field with today's date

6. **Validate JSON** syntax before committing

### Modifying Existing Cases

- Keep the `id` unchanged to maintain references
- Update `last_updated` date
- Test changes thoroughly
- Document changes in version history if applicable

### Adding Images

- Place images in the correct category folder: `assets/images/{category}/`
- Use clear, descriptive filenames
- Ensure medical accuracy and clarity
- Reference the new image path in the case's `adults_media` or `child_media` object

## Disclaimer

**This dataset is for educational purposes only.** It provides general first aid guidance and is not a substitute for professional medical advice, diagnosis, or treatment.

**Important:**

- Always seek immediate professional medical help for emergencies
- This information does not replace certified first aid training
- Medical conditions vary; consult qualified healthcare professionals for individual assessment
- Users are responsible for following local emergency protocols and contacting emergency services
- The creators and maintainers are not liable for any harm resulting from the use of this dataset

In case of emergency, always call your local emergency number immediately.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
