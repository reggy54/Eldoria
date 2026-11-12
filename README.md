# Эльдория для Android

В папке `www` лежит вся игра (один файл `index.html`) с манифестом, офлайн-кэшем и иконками.
Есть два способа получить APK.

## Способ 1. Android Studio (Capacitor)
Нужны: Node.js 18+, Android Studio (с Android SDK), JDK 17.

    npm install
    npx cap add android
    npx cap sync android
    npx cap open android

В Android Studio: Build → Build Bundle(s) / APK(s) → Build APK(s).
Готовый файл: `android/app/build/outputs/apk/debug/app-debug.apk`.
Для магазина выберите Build → Generate Signed Bundle / APK и подпишите своим ключом.

Совет: чтобы игра запускалась в горизонтальной ориентации, в `android/app/src/main/AndroidManifest.xml`
добавьте к `<activity>` атрибут `android:screenOrientation="sensorLandscape"`.

## Способ 2. PWABuilder (без Android Studio)
1. Выложите содержимое папки `www` на любой хостинг с HTTPS (GitHub Pages, Netlify, Cloudflare Pages).
2. Откройте pwabuilder.com, вставьте адрес и нажмите Package for stores → Android.
3. Скачайте готовый APK/AAB.

## Важно
- Шрифты подключаются с Google Fonts. Без интернета при первом запуске игра покажет системные шрифты
  (всё работает, но выглядит чуть проще). Чтобы шрифты были и офлайн, скачайте Philosopher и Alegreya Sans
  и подключите через @font-face в `index.html`.
- Прогресс хранится в localStorage приложения. Слоты и экспорт сохранения есть в «Меню → Сохранение».

## Версия 1.1
Мир до 90 уровня, 6 классов, ездовые (конь, лодка, грифон), питомцы, профессии, рыбалка, события, сюжет «Сердце Эльдора»,
Бездна, арена, доска розыска, музыка и звуки. Старые сохранения совместимы.
Звук включается после первого касания экрана. Кэш обновляется сам: при выходе новой версии игра подтянет её при запуске с интернетом.
