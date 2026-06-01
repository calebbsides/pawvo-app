# Play Console Submission Checklist

Step-by-step guide for submitting Pawvo to Google Play.

---

## Before you start

- [ ] Pay $25 registration fee at play.google.com/console
- [ ] Identity verification complete (Google may take up to 2 business days)
- [ ] Privacy policy hosted at a live public URL (see play-store-listing.md)
- [ ] 512×512 app icon PNG ready (see Icon section below)
- [ ] Feature graphic ready (1024×500 PNG, see below)
- [ ] At least 2 phone screenshots ready (see below)
- [ ] At least 1 Wear OS screenshot ready

---

## Step 1 — Create the app

1. Play Console → **All apps** → **Create app**
2. App name: `Pawvo – Pet Voice Translator`
3. Default language: English (United States)
4. App or game: **App**
5. Free or paid: **Free**
6. Tick both declarations → **Create app**

---

## Step 2 — Store listing

**App and store details (left nav)**

| Field | Value |
|---|---|
| App name | Pawvo – Pet Voice Translator |
| Short description | Hear what your pet is saying — AI-powered voice translation for dogs & cats. |
| Full description | (paste from play-store-listing.md) |

**Graphics**

| Asset | Spec | Notes |
|---|---|---|
| App icon | 512×512 PNG, no alpha, no rounded corners | Export from Android Studio: right-click `ic_launcher` → Image Asset → Export |
| Feature graphic | 1024×500 PNG or JPG | A branded banner; no text overlap with Google overlays at edges |
| Phone screenshots | 2–8 screenshots, 16:9 or 9:16, min 320dp short side | Take from the running app: Auth screen, Home/conversation screen |
| Wear OS screenshots | 1–8 screenshots, square 1:1 | Take from the Wear OS emulator |

**Categorization**

| Field | Value |
|---|---|
| App category | Tools |
| Tags | pet translator, dog translator, AI pet |

**Contact details**

| Field | Value |
|---|---|
| Email | calebbsides@gmail.com |
| Privacy policy | (your hosted URL for privacy-policy.html) |

---

## Step 3 — App content (left nav → App content)

Complete each section:

### Privacy policy
Paste your hosted privacy policy URL.

### Ads
No, the app does not contain ads.

### App access
All or most functionality is available without special access.

### Content rating
1. Click **Start questionnaire**
2. Category: **Utility / Productivity**
3. Answer the questions:
   - Violence: **No**
   - Sexual content: **No**
   - Language: **No**
   - Controlled substances: **No**
   - User-generated content: **No** (transcripts are AI-generated, not shared between users)
   - Location sharing: **Yes** — shares location with the developer (used for environmental context)
   - Personal info: **Yes** — collects email address
   - Result should be: **Everyone (E)**

### Target audience and content
- Target age group: **18 and over**
- Appeals to children: **No**

### News apps
Not a news app.

### COVID-19 contact tracing
Not applicable.

### Data safety ← IMPORTANT, see detail below

---

## Step 4 — Data Safety section

Fill in each data type:

### Does your app collect or share any of the required user data types?
**Yes**

### Data types collected or shared:

| Category | Type | Collected | Shared | Ephemeral | Required |
|---|---|---|---|---|---|
| Location | Precise location | Yes | No | No | No (optional, for context) |
| Location | Approximate location | Yes | No | No | No (optional, for context) |
| Personal info | Name | Yes | No | No | Yes (account) |
| Personal info | Email address | Yes | No | No | Yes (account) |
| Personal info | User IDs | Yes | No | No | Yes (account) |
| Audio | Voice or sound recordings | Yes | Yes | No | Yes (core feature) |
| App activity | App interactions | Yes | No | No | No |

### For "Voice or sound recordings":
- Collected: **Yes**
- Shared: **Yes** — shared with Groq, Inc. for AI speech-to-text processing
- Ephemeral: **No** — stored as session transcripts for 90 days
- Required for basic app function: **Yes**
- Purpose: **App functionality**

### For "Precise location":
- Collected: **Yes**
- Shared: **No** (stays within our infrastructure)
- Ephemeral: **No** — retained with session context
- Required: **No** (permission can be denied)
- Purpose: **App functionality** (environmental context for AI)

### Security practices:
- Data is encrypted in transit: **Yes**
- You provide a way for users to request that their data be deleted: **Yes** (contact email in privacy policy)

---

## Step 5 — Releases

### Phone app
1. Left nav → **Production** → **Create new release**
2. Upload: `android/app/build/outputs/bundle/release/app-release.aab`
3. Release name: `1.0 (1)`
4. Release notes (What's new):
   ```
   Initial release of Pawvo — give your pet a voice with AI-powered translation.
   ```
5. Save → **Review release**

### Wear OS app
1. Left nav → **Wear OS** tab (appears automatically after uploading the phone AAB)
   - If not visible: left nav → **Advanced settings** → **Device targeting** or look under **Production** for a Wear OS sub-track
2. Upload: `android/wear/build/outputs/bundle/release/wear-release.aab`
3. Same release notes as above

---

## Step 6 — Pricing & distribution

- Countries: select all or start with United States
- Paid/Free: Free
- Contains ads: No

---

## Step 7 — Review and submit

1. Left nav → **Publishing overview**
2. Fix any warnings shown (typically missing screenshots or incomplete sections)
3. **Send for review**
4. Review takes 1–7 business days for a new app

---

## Taking screenshots

**Phone screenshots (from Android Studio):**
1. Run the app on the emulator (staging build variant → points at live AWS backend)
2. Log in, create a pet, open the conversation screen
3. In Android Studio emulator toolbar: camera icon → saves PNG to Desktop
4. Repeat for: Auth screen, Home screen with a pet, Conversation/transcript view, Settings

**Wear OS screenshots:**
1. Run the Wear OS emulator
2. Install the wear app: `adb -s emulator-5556 install wear-debug.apk`
3. Launch it, grant permissions
4. Screenshot: emulator toolbar → camera icon

**512×512 app icon:**
In Android Studio: right-click `app/src/main/res` → **New → Image Asset** → set source to `ic_launcher_foreground.xml`, output 512×512 → export. Or generate from the SVG using any image editor.

---

## After approval

- App goes live on Play Store automatically after approval unless you set a staged rollout
- For staged rollout: under Release → edit rollout % (e.g. 20% first, then increase)
- Wear OS app will auto-install on paired Wear OS watches when users install the phone app
