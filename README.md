name: Build Android APK
on: [push, workflow_dispatch]

jobs:
  build:
    name: Build APK
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Repository
        uses: actions/checkout@v4

      - name: Set up Java
        uses: actions/setup-java@v3
        with:
          distribution: 'zulu'
          java-version: '17'

      - name: Set up Flutter
        uses: subosito/flutter-action@v2
        with:
          channel: 'stable'

      - name: Install Dependencies
        run: flutter pub get

      - name: Build APK
        run: flutter build apk --debug

      - name: Upload APK Artifact
        uses: actions/upload-artifact@v4
        with:
          name: Android-App-Package
          path: build/app/outputs/flutter-apk/app-debug.apk
# probable-succotash
It's a sci-fi thriller game 
