فخليني أشرحلك الطريقة السريعة باستخدام MobaXterm لنقل صورة Docker (.tar) من السيرفر إلى اللابتوب، ثم رفعها من Windows.
✅ أولًا: حفظ صورة Docker داخل السيرفر كملف .tar

في نافذة MobaXterm (SSH على السيرفر)، نفّذ:

docker save -o bee-quotes-app.tar eltohami/bee-quotes-app:v1

ده هيحفظ الصورة في ملف اسمه bee-quotes-app.tar في نفس المسار اللي إنت واقف فيه.
✅ ثانيًا: انقل الملف من السيرفر للويندوز
📦 في نفس شاشة MobaXterm:

لو كنت متصل بـ SSH، هتلاقي على اليسار نافذة file browser تلقائية فيها كل ملفات السيرفر.

    ابحث عن bee-quotes-app.tar في المجلد اللي حفظته فيه (مثلاً /home/ahmed أو ~/)

    اسحب الملف للفولدر اللي عايز تحطه فيه على Windows (مثلاً سطح المكتب)

✨ سهل جدًا! مفيش أوامر نقل ولا حاجة، مجرد Drag & Drop.
✅ ثالثًا: على Windows – تحميل ورفع الصورة على Docker
1. افتح CMD أو PowerShell وتأكد إن Docker Desktop شغال
2. حمّل الصورة:

docker load -i "C:\Users\YourUsername\Desktop\bee-quotes-app.tar"

غير المسار حسب مكان الملف.
3. تأكد إنها اتعملها load:

docker images

4. لو لقيت الصورة من غير tag، ضيفه:

docker tag bee-quotes-app eltohami/bee-quotes-app:v1

5. سجل الدخول:

docker login

6. ارفع الصورة:

docker push eltohami/bee-quotes-app:v1

🔚 كده الصورة اتنقلت من السيرفر إلى Windows واترفعت على Docker Hub بدون مشاكل في بطء الشبكة.

لو حابب أجهزلك ملف أو خطوات جاهزة مكتوبة تنفذ منها على طول قولي، أو لو تحب نبدأ في التطبيق سوا خطوة بخطوة.
