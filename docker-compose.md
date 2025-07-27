✅ 📦 المهمة الرئيسية:

تشغيل تطبيق Flask بسيط + MySQL باستخدام Docker Compose.
🧱 أولًا: الملفات اللي أنشأناها
1. app.py

كود تطبيق Flask بسيط جدًا:

from flask import Flask
app = Flask(__name__)

@app.route('/')
def home():
    return "Hello from Docker + Flask!"

if __name__ == "__main__":
    app.run(host='0.0.0.0', port=5000)

2. requirements.txt

flask

3. Dockerfile

FROM python:3.9-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
CMD ["python", "app.py"]

4. docker-compose.yml (البورت 5001 بدل 5000 عشان نتفادى التعارض)

version: '3.8'

services:
  web:
    build: .
    ports:
      - "5001:5000"
    depends_on:
      - db

  db:
    image: mysql:5.7
    environment:
      MYSQL_ROOT_PASSWORD: rootpass
      MYSQL_DATABASE: mydb

🔧 ثانياً: الخطوات اللي نفذناها
1. تثبيت Docker و Docker Compose على Red Hat

(عملناها قبل كده، واتأكدنا إن كل حاجة شغّالة)
2. عملنا Build و Run للمشروع:

docker compose up -d

شغّلنا كل الخدمات في الخلفية.
3. تأكدنا من التشغيل:

    شوفنا الـ containers شغّالة:

docker compose ps

    جربنا التطبيق باستخدام:

curl http://localhost:5001

وظهر:

Hello from Docker + Flask!

4. فهمنا:

    إزاي Dockerfile بيبني صورة للتطبيق.

    ليه استخدمنا ports بالشكل 5001:5000.

    إزاي docker-compose.yml بيشغل أكتر من خدمة (web + db).

    إزاي نتابع اللوجات باستخدام docker compose logs.

✅ كده خلصنا اليوم الخاص بـ Docker Compose

والمشروع بقى شغّال تمام.
