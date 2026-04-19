<<<<<<< HEAD
# AptoSwasthy — Your Personal Health Intelligence App

AptoSwasthy is an iOS app that acts like a personal health advisor in your pocket. It tracks your health metrics, analyzes your habits, estimates your life expectancy, and gives you personalized recommendations — all powered by an AI assistant called **Pearl**.

Think of it as your smart health dashboard: connect it to Apple Health, log your meals, import blood test results, and Pearl will make sense of it all for you.

---

## What the App Does

- **Health Dashboard** — See all your key health stats (heart rate, steps, sleep, blood pressure, weight, and more) in one place
- **Pearl AI Chat** — Ask Pearl anything about your health and get personalized, data-driven answers
- **Life Expectancy Estimate** — See a running estimate of your lifespan based on your actual health data, and which habits are helping or hurting it
- **Disease Risk Assessment** — Get a clear breakdown of your risk for common conditions based on your profile and metrics
- **Nutrition Logger** — Log meals by searching foods or scanning barcodes; see your nutrition score
- **Habit Tracker** — Pearl recommends personalized health habits and tracks your progress
- **3D Body Visualization** — See a visual body model that reflects your height, weight, and body composition
- **Blood Test Import** — Upload your lab results and Pearl will analyze them for you
- **Apple Health Sync** — Automatically pulls in data from your iPhone's Health app

---

## What You'll Need Before Starting

You need a **Mac computer** to build and run this app (iPhones can't build apps by themselves). Here's everything you need:

| What | Why | Free? |
|------|-----|-------|
| A Mac running macOS 14 (Sonoma) or newer | Required to run Xcode | Yes (comes with Mac) |
| **Xcode 16** or newer | Apple's tool for building iPhone apps | Yes (free from App Store) |
| An Apple ID | Required to run the app on your phone | Yes |
| An iPhone running **iOS 18** or newer | To test on a real device (optional — simulator works too) | You likely already have one |
| **Homebrew** | A package manager for Mac (makes installing tools easy) | Yes |
| **XcodeGen** | A tool that sets up the Xcode project file | Yes |

---

## Step-by-Step Setup Guide

### Step 1 — Install Xcode

1. Open the **App Store** on your Mac
2. Search for **Xcode**
3. Click **Get** and then **Install** (it's a large download — around 15GB, so give it time)
4. Once installed, open Xcode once to accept the license agreement, then close it

### Step 2 — Install Homebrew

Homebrew is like an "app store for developer tools." You only need to do this once.

1. Open the **Terminal** app on your Mac (search for "Terminal" in Spotlight — press `⌘ + Space` and type "Terminal")
2. Paste this entire command and press **Enter**:

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

3. Follow the on-screen prompts (it may ask for your Mac password)
4. When it finishes, close Terminal and reopen it

### Step 3 — Install XcodeGen

XcodeGen is a small tool that generates the Xcode project file from a configuration file. Run this in Terminal:

```
brew install xcodegen
```

Wait for it to finish. You'll see a success message when done.

### Step 4 — Download the App Code

If you received the code as a ZIP file:
1. Double-click the ZIP to extract it
2. Move the extracted folder somewhere easy to find (like your Desktop or Documents)

If you're cloning from GitHub:
```
git clone https://github.com/YOUR-USERNAME/YOUR-REPO-NAME.git
```

### Step 5 — Generate the Xcode Project

1. Open **Terminal**
2. Navigate to the `AptoSwasthy` folder inside the project. For example, if you put the project on your Desktop:

```
cd ~/Desktop/APP/AptoSwasthy
```

3. Run this command:

```
xcodegen generate
```

You should see output ending in something like `✓ Generated project at AptoSwasthy.xcodeproj`. This creates the Xcode project file.

### Step 6 — Open the Project in Xcode

Still in Terminal, run:

```
open AptoSwasthy.xcodeproj
```

Xcode will open. Give it a minute to load and index the project files.

### Step 7 — Set Your Development Team

This tells Xcode which Apple account to use for running the app.

1. In Xcode, click on **AptoSwasthy** in the left sidebar (the blue icon at the very top)
2. In the main area, click the **Signing & Capabilities** tab
3. Under **Team**, click the dropdown and select your Apple ID
   - If you don't see your Apple ID, go to **Xcode → Settings → Accounts** and add it with the `+` button

> **Note:** With a free Apple ID, you can run the app on your own iPhone for up to 7 days before needing to re-install. A paid Apple Developer account ($99/year) removes this limit and lets you distribute the app.

### Step 8 — Run the App

**On the iOS Simulator (no iPhone needed):**
1. At the top of Xcode, click the device selector (it shows something like "iPhone 15" or "Any iOS Device")
2. Choose an iPhone model from the list (e.g., **iPhone 16 Pro**)
3. Press the **Play button** (▶) or press `⌘ + R`
4. The simulator will launch and the app will open automatically

**On your real iPhone:**
1. Connect your iPhone to your Mac with a cable
2. Select your iPhone from the device selector at the top of Xcode
3. On your iPhone, go to **Settings → General → VPN & Device Management** and trust your Apple ID
4. Press the **Play button** (▶) or press `⌘ + R`

The first build takes a few minutes. Subsequent builds are much faster.

---

## First Time Using the App

When you first open AptoSwasthy:

1. **Create an account** — Sign up with your email address. You'll receive a verification code.
2. **Grant permissions** — The app will ask for access to:
   - **Apple Health** — to read your health data (steps, heart rate, sleep, etc.)
   - **Camera** — for barcode scanning when logging food
   - **Face ID** — for secure login (optional)
   - **Notifications** — for habit reminders (optional)
3. **Complete onboarding** — Answer questions about your health, lifestyle, and goals. This helps Pearl give you personalized insights.
4. **Explore!** — Your dashboard will start populating once the app reads your Apple Health data.

---

## Troubleshooting

**"No such module" error in Xcode**
→ Make sure you ran `xcodegen generate` in the `AptoSwasthy` folder before opening Xcode.

**"Signing certificate" error**
→ Go to **Signing & Capabilities** in Xcode and make sure your Apple ID is selected under **Team**.

**App crashes immediately on launch**
→ Make sure your device or simulator is running **iOS 18 or newer**.

**Build fails with "Swift compiler" errors**
→ Make sure you have **Xcode 16 or newer**. Go to **Xcode → About Xcode** to check your version.

**"Could not launch app" on real iPhone**
→ On your iPhone, go to **Settings → General → VPN & Device Management**, find your Apple ID, and tap **Trust**.

**Simulator is very slow**
→ Try a different simulator — iPhones with "Pro" in the name tend to perform better. Also make sure your Mac has at least 8GB of RAM.

---

## Project Structure (for the curious)

```
APP/
├── AptoSwasthy/          — The iOS app code
│   ├── Sources/          — All Swift source code
│   │   ├── App/          — App entry point and main navigation
│   │   ├── AI/           — Pearl chat interface
│   │   ├── Pearl/        — Pearl's health analysis engines
│   │   ├── Home/         — Dashboard, habits, nutrition logger
│   │   ├── Risks/        — Disease risk assessment
│   │   ├── You/          — Profile and 3D body model
│   │   ├── Authentication/ — Login, sign up, password reset
│   │   ├── Services/     — Apple Health, data storage, notifications
│   │   └── Models/       — Data structures (User, Meal, Habit, etc.)
│   ├── infra/            — Backend server code (AWS Lambda)
│   └── project.yml       — Xcode project configuration
├── caesar-norm-wsx/      — Body shape model data (for 3D visualization)
├── appicon.png           — App icon reference
└── README.md             — This file
```
=======
# APP-APTOSWASTHY
>>>>>>> 30ee278dad31714af55c0cb8658ad37001abd533
