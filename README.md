# Trekky — Subscription Tracker

> Never lose track of what you're paying for.

Trekky is a free iOS app for managing all your subscriptions in one place. Built because keeping track of monthly costs shouldn't require yet another subscription.

<img width="310" height="134" alt="Bildschirmfoto 2026-06-20 um 00 57 59" src="https://github.com/user-attachments/assets/e455ac75-2154-4cec-a4b0-8d4940907f0b" />


---

## Features

- **Subscription overview** — Add and manage unlimited subscriptions with name, price, billing cycle, and category
- **Auto logos** — Company logos are loaded automatically via domain name (no manual setup needed)
- **Cost overview** — See your total monthly and yearly spend at a glance, with charts
- **Calendar view** — Visual calendar showing exactly when each subscription is billed
- **Billing reminders** — Get notified 1 day before a charge hits your account
- **Cancellation deadlines** — Set cancellation windows and get reminded before they expire
- **mydealz integration** — Automatically shows current deals for your tracked services
- **iCloud sync** — Your subscriptions are available across all your devices
- **Cancelled archive** — Cancelled subscriptions are archived, not deleted
- **Dark mode** — Dark-first design

---

## Screenshots

| Home | Finance Overview | Calendar | Settings |
|------|-----------------|----------|----------|
|<img width="1242" height="2688" alt="Simulator Screenshot - iPhone 11 Pro Max - 2026-06-09 at 12 49 49" src="https://github.com/user-attachments/assets/90ebc43e-622f-4de6-b2c9-6102fe4bfc44" /> | <img width="1242" height="2688" alt="Simulator Screenshot - iPhone 11 Pro Max - 2026-06-09 at 12 49 34" src="https://github.com/user-attachments/assets/e713e4cd-1bf7-4b31-8391-ac1f624bf9a2" /> | <img width="1242" height="2688" alt="Simulator Screenshot - iPhone 11 Pro Max - 2026-06-09 at 19 23 27" src="https://github.com/user-attachments/assets/2a6f089e-5492-4573-9db7-0ae9980bc825" /> | <img width="1242" height="2688" alt="Simulator Screenshot - iPhone 11 Pro Max - 2026-06-09 at 12 49 26" src="https://github.com/user-attachments/assets/e199ae6a-f183-42a9-b2b1-3213562f4cd1" /> |

---

## Trekky Pro

Trekky is free to use with a 7-day trial. After that, a **one-time purchase of €4.99** unlocks everything — no subscription, no recurring fees.

**Pro includes:**
- Unlimited subscriptions
- Billing & cancellation notifications
- iCloud sync
- All future updates

---

## Tech Stack

| | |
|---|---|
| **UI** | SwiftUI |
| **Concurrency** | Swift async/await (no Combine) |
| **Persistence** | UserDefaults (JSON-encoded) |
| **Notifications** | UNUserNotificationCenter |
| **In-App Purchase** | StoreKit 2 |
| **Logo loading** | Clearbit · Google Favicons · DuckDuckGo |

---

## Requirements

- Xcode 16+
- iOS 17+

---

## Getting Started

```bash
git clone https://github.com/noheartanthony/trekky.git
cd trekky
open Trekky.xcodeproj
```

Select the `Trekky` scheme, choose a simulator or device, and run. No additional dependencies or package setup needed.

> **Note:** In-app purchases require a real device and an active App Store Connect configuration. The included `.storekit` file lets you test purchases locally in the simulator.

---

## Project Structure

```
Trekky/
├── Subscription.swift          # Data model (Codable, Identifiable)
├── SubscriptionManager.swift   # CRUD + notification scheduling
├── PurchaseManager.swift       # StoreKit 2 purchase logic
├── NotificationManager.swift   # UNUserNotificationCenter wrapper
├── ImageCacheManager.swift     # Logo fetching + memory/disk cache
├── AppearanceManager.swift     # Color scheme preference
└── Views/
    ├── HomeView                # Main list + FAB
    ├── FinanzübersichtView     # Charts + cost breakdown
    ├── AddSubscriptionView     # Add new subscription (+ templates)
    ├── EditSubscriptionView    # Edit existing subscription
    ├── SubscriptionDetailView  # Detail + cancellation reminders
    ├── SettingsView            # App settings
    ├── OnboardingView          # First-launch onboarding
    ├── PaywallView             # Pro purchase screen
    └── DealsView               # mydealz deals
```

