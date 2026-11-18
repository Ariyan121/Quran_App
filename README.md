# কোরআন শরীফ – Android প্রজেক্ট

আরবি পাঠ ও বাংলা অনুবাদসহ ১১৪টি সূরার অফলাইন রিডার। অ্যাপটি ইন্টারনেট ছাড়াই চলে, কারণ ডেটা ও ফন্ট দুটোই অ্যাপের ভেতরে আছে।

## APK বানানোর ধাপ (নিজের কম্পিউটারে)

দরকার: Node.js (18+) এবং Android Studio।

1. এই ফোল্ডারে টার্মিনাল খুলে চালান: `npm install`
2. `npx cap sync android`
3. `npx cap open android` (Android Studio-তে প্রজেক্ট খুলবে। প্রথমবার Gradle সিঙ্ক শেষ হতে কয়েক মিনিট লাগে)
4. টেস্ট APK: মেনু থেকে Build > Build Bundle(s) / APK(s) > Build APK(s)
5. ফোনে ইনস্টল করে চালিয়ে দেখুন।

## Play Store-এ দেওয়ার আগে

- `capacitor.config.json`-এ `appId` বদলে নিজের অনন্য আইডি দিন (যেমন `com.yourname.quran`), তারপর আবার `npx cap sync android` চালান।
- Android Studio থেকে Build > Generate Signed Bundle / APK দিয়ে সই করা AAB বানান।
- নিজস্ব অ্যাপ আইকন দিন (Android Studio: res > New > Image Asset)।
- আরবি আয়াত ও বাংলা অনুবাদ নির্ভরযোগ্য ছাপা কোরআনের সঙ্গে মিলিয়ে, সম্ভব হলে একজন আলেমকে দিয়ে যাচাই করুন।

## ডেটা ও লাইসেন্স

আরবি পাঠ ও বাংলা অনুবাদ: quran-json ডেটাসেট (CC BY 4.0)। ফন্ট: Amiri Quran ও Noto Sans Bengali (SIL Open Font License, @fontsource থেকে)। প্রকাশের সময় অ্যাপে এই উৎস-স্বীকৃতি রাখতে হবে (অ্যাপের নিচে আছে)।

## ফাইল

- `www/index.html` – পুরো অ্যাপ (UI + ডেটা)
- `www/fonts/` – অফলাইন ফন্ট
- `android/` – Capacitor-জেনারেটেড Android Studio প্রজেক্ট

## কম্পিউটারে সফটওয়্যার ইনস্টল ছাড়া APK বানানো (GitHub Actions)

1. github.com-এ বিনামূল্যে অ্যাকাউন্ট খুলে একটি নতুন রিপোজিটরি বানান।
2. এই ফোল্ডারের সব ফাইল (`.github` ফোল্ডারসহ) রিপোজিটরির `main` ব্রাঞ্চে আপলোড করুন।
3. রিপোজিটরির Actions ট্যাবে "Build Android APK" চালু হবে (না হলে Run workflow চাপুন)।
4. কয়েক মিনিট পর কাজ শেষ হলে ওই রানের পেজ থেকে `quran-debug-apk` ডাউনলোড করুন। ভেতরে `app-debug.apk` পাবেন।
5. ফোনে ইনস্টল করতে "অজানা উৎস থেকে ইনস্টল" অনুমতি দিতে হবে।

এটা টেস্ট (debug) APK। Play Store-এর জন্য সই করা AAB লাগবে, সেটা আলাদা ধাপ।
