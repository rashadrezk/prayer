# متابعة الصلاة — خطوات التشغيل (كلها مجانية، حوالي 10 دقايق)

## 1) أنشئ قاعدة البيانات (Firebase)
1. ادخل https://console.firebase.google.com بحساب جوجل واضغط **Add project** (ممكن تقفل Google Analytics).
2. من القائمة: **Build → Firestore Database → Create database** → اختار أي منطقة → **Start in production mode**.
3. من تبويب **Rules** الصق ده واضغط Publish:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /groups/{group}/days/{day} {
      allow read, write: if true;
    }
  }
}
```
(الأمان هنا قائم على إن كود العيلة سرّي وصعب تخمينه، فاختار كود طويل.)

4. من **Project settings (⚙️) → General → Your apps → أيقونة الويب `</>`** سجّل تطبيق ويب، وهيطلعلك `firebaseConfig`.
5. انسخ القيم (apiKey, authDomain, projectId, appId) وحطها في أول سكريبت جوّه `index.html` مكان `PASTE_HERE`.

## 2) انشر الموقع (Netlify Drop — أسهل حاجة)
1. ادخل https://app.netlify.com/drop
2. اسحب فولدر المشروع كله (index.html + manifest.json + sw.js + icon.svg).
3. هياخد لينك مجاني زي `https://xxxx.netlify.app`.

## 3) الاستخدام
- **عندك إنت:** افتح اللينك → اختار **متابِع** → اكتب كود العيلة (مثلاً `ahmed-family-482`).
- **عند إخواتك:** افتح نفس اللينك → اختار **هصلّي وأسجّل** → نفس الكود + اسمه.
- **الموبايل اللي هتديله لقريبك:** يدخل بنفس الكود، ويضغط **＋ شخص** ويكتب اسم ابنه.
- على أندرويد: من قائمة كروم (⋮) اختار **Add to Home screen** فيشتغل زي التطبيق.
