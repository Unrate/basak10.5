# Android Studio Kurulum Rehberi

## 1. Projeyi Android Studio'ya Aktarma

### Gereksinimler
- Android Studio (en son sürüm)
- Node.js (v18 veya üzeri)
- Expo CLI
- EAS CLI

### Kurulum Adımları

1. **EAS CLI'yi yükleyin:**
```bash
sudo npm install -g @expo/cli eas-cli
```

2. **Expo hesabınıza giriş yapın:**
```bash
expo login
```

3. **Development build oluşturun:**
```bash
eas build --profile development --platform android
```

4. **Yerel development build için:**
```bash
eas build --profile development --platform android --local
```

## 2. Android Studio Konfigürasyonu

### Gerekli SDK'lar
- Android SDK Platform 34
- Android SDK Build-Tools 34.0.0
- Android Emulator
- Intel x86 Emulator Accelerator (HAXM installer)

### Environment Variables
Aşağıdaki environment variable'ları sisteminize ekleyin:

```bash
export ANDROID_HOME=$HOME/Android/Sdk
export PATH=$PATH:$ANDROID_HOME/emulator
export PATH=$PATH:$ANDROID_HOME/platform-tools
```

## 3. Geliştirme Süreci

### Development Server Başlatma
```bash
npx expo start --dev-client
```

### Android Emulator'da Çalıştırma
```bash
npx expo run:android
```

### Fiziksel Cihazda Test
1. USB Debugging'i etkinleştirin
2. Cihazı bilgisayara bağlayın
3. `npx expo run:android` komutunu çalıştırın

## 4. Native Kod Değişiklikleri

Eğer native Android kodu değiştirmeniz gerekiyorsa:

1. **Prebuild çalıştırın:**
```bash
npx expo prebuild --platform android
```

2. **Android klasörü oluşturulduktan sonra Android Studio'da açın**

3. **Native değişikliklerinizi yapın**

4. **Tekrar build alın:**
```bash
npx expo run:android
```

## 5. Önemli Notlar

- Bu proje Expo Router kullanıyor, bu yüzden navigation yapısı farklı olabilir
- Native modüller eklerken `expo install` kullanın
- Config değişikliklerinden sonra `npx expo prebuild --clean` çalıştırın
- Development build kullandığınız için OTA updates çalışmayacak

## 6. Debugging

### React Native Debugger
```bash
npm install -g react-native-debugger
```

### Flipper Integration
Flipper otomatik olarak development build'lerde aktif olacak.

## 7. Build Alma

### APK Build
```bash
eas build --profile preview --platform android
```

### AAB Build (Play Store için)
```bash
eas build --profile production --platform android
```

## Sorun Giderme

### Metro Cache Temizleme
```bash
npx expo start --clear
```

### Node Modules Temizleme
```bash
rm -rf node_modules
npm install
```

### Expo Cache Temizleme
```bash
expo r -c
```