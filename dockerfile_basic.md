🎯 الـ Task: Dockerfile
المطلوب:

1-أنشئ فولدر جديد اسمه myapp.

2-جوه الفولدر اعمل ملف index.html مكتوب فيه: 
       
    Hello from my custom Docker image
3-اكتب Dockerfile بيستخدم nginx كـ base image.

4-انسخ index.html جوه مسار /usr/share/nginx/html/ داخل الـ image.

5-ابني image جديدة باسم custom-nginx:v1.

6-شغّل container من الـ image الجديدة على بورت 9090.

7-اتأكد إن الصفحة بتظهر لما تدخل على: http://localhost:9090

_____________
📝 الحل مع الشرح
1- إنشاء فولدر المشروع

    mkdir myapp
    cd myapp
______
2- إنشاء ملف HTML

     echo "Hello from my custom Docker image" > index.html
_______
3- إنشاء Dockerfile

افتح ملف اسمه Dockerfile بالمحتوى ده:

     # نبدأ من image جاهزة: nginx
    FROM nginx:latest

    # ننسخ ملف index.html بتاعنا لجوه مكان ملفات nginx
    COPY index.html /usr/share/nginx/html/index.html

🔎 شرح:

  FROM nginx:latest → بيبدأ من nginx official image.

  COPY → بينسخ الملف من جهازك إلى داخل الـ image.
______
4-بناء الـ Image

    docker build -t custom-nginx:v1 .
🔎 شرح:

-t → لتسمية الـ image.

. → معناها ابني من الـ Dockerfile الموجود في الفولدر الحالي.

_______
5-تشغيل Container

     docker run -d --name webapp -p 9090:80 custom-nginx:v1
🔎 شرح:

بيربط بورت 9090 من جهازك مع بورت 80 جوه الـ container.
_______
6-التحقق

      curl http://localhost:9090

الناتج هيكون:

     Hello from my custom Docker image
✅✅✅✅✅✅



















