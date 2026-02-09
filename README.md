[![pub package](https://img.shields.io/pub/v/postal_ko.svg?label=postal_ko&color=blue)](https://pub.dev/packages/postal_ko)
[![Pub Likes](https://img.shields.io/pub/likes/postal_ko)](https://pub.dev/packages/postal_ko/score)
[![Test](https://github.com/coco-de/postal_ko/actions/workflows/test.yml/badge.svg)](https://github.com/coco-de/postal_ko/actions/workflows/test.yml)

[![English](https://img.shields.io/badge/Language-English-9cf?style=for-the-badge)](README.md)
[![Korean](https://img.shields.io/badge/Language-Korean-9cf?style=for-the-badge)](README.ko-kr.md)

# 🚀 postal_ko

A **cross-platform** Flutter package for Korean postal address search using [Kakao postcode service](https://postcode.map.kakao.com/guide).

## ✨ Features

- 📱 **Cross-platform support**: Works seamlessly on **mobile** (iOS/Android) and **web** platforms
- 🔍 **Korean address search**: Powered by Kakao postcode service
- 🌐 **Web integration**: Native web support with DOM manipulation
- 📍 **Geocoding support**: Get latitude/longitude coordinates
- 🛡️ **Null-safe**: Full null safety support
- 🎯 **Unified API**: Single package for all platforms

<div><img src="https://tykann.github.io/kpostal/assets/screenshot.png" width="375"></div>

## 🚀 Getting Started

Add postal_ko to your pubspec.yaml file:

```yaml
dependencies:
  postal_ko: ^1.1.0
```

## 📱 Platform Support

| Platform    | Support | Notes                        |
| ----------- | ------- | ---------------------------- |
| **Android** | ✅      | Requires internet permission |
| **iOS**     | ✅      | Full support                 |
| **Web**     | ✅      | Native web integration       |
| **macOS**   | ❌      | Not supported                |
| **Windows** | ❌      | Not supported                |
| **Linux**   | ❌      | Not supported                |

## ⚙️ Setup

### 🤖 Android

Add internet permission to your `AndroidManifest.xml`:

```xml
<uses-permission android:name="android.permission.INTERNET"/>
```

### 🍎 iOS

No additional setup required for basic usage.

### 🌐 Web

No additional setup required. The package automatically handles web integration.

### 🔧 Local Server (Optional)

If you want to use local server hosting:

#### Android

Add `android:usesClearextTraffic="true"` to your `AndroidManifest.xml`:

```xml
<application
    android:label="[your_app]"
    android:icon="@mipmap/ic_launcher"
    android:usesCleartextTraffic="true">
    ...
</application>
```

#### iOS

Add `NSAppTransportSecurity` to your `info.plist`:

```xml
<key>NSAppTransportSecurity</key>
<dict>
    <key>NSAllowsArbitraryLoads</key>
    <true/>
</dict>
```

### 🗺️ Kakao Geocoding (Optional)

1. Go to [Kakao Developer Site](https://developers.kakao.com)
2. Register developer and create app
3. Add Web Platform and register domain:
   - Default: `https://tykann.github.io`
   - Local server: `http://localhost:8080`
4. Use the JavaScript key as `kakaoKey`

## 📖 Usage

### Basic Usage

```dart
import 'package:postal_ko/postal_ko.dart';

// Using callback
TextButton(
  onPressed: () async {
    await Navigator.push(
      context,
      MaterialPageRoute(
        builder: (_) => KpostalView(
          callback: (Kpostal result) {
            print('Address: ${result.address}');
            print('Postal Code: ${result.postCode}');
            print('Coordinates: ${result.latitude}, ${result.longitude}');
          },
        ),
      ),
    );
  },
  child: Text('Search Address'),
)

// Using return value
TextButton(
  onPressed: () async {
    Kpostal? result = await Navigator.push(
      context,
      MaterialPageRoute(builder: (_) => KpostalView()),
    );
    if (result != null) {
      print('Selected address: ${result.address}');
    }
  },
  child: Text('Search Address'),
)
```

### Advanced Usage

```dart
KpostalView(
  useLocalServer: true, // Use local server (default: false)
  localPort: 8080, // Local server port (default: 8080)
  kakaoKey: 'your_kakao_js_key', // Optional Kakao geocoding
  callback: (Kpostal result) {
    // Handle result
    print('Address: ${result.address}');
    print('Building name: ${result.buildingName}');
    print('Zone code: ${result.zonecode}');
    print('Coordinates: ${result.latitude}, ${result.longitude}');
  },
)
```

## 📊 Kpostal Model

```dart
class Kpostal {
  String postCode;        // Postal code
  String address;         // Full address
  String jibunAddress;    // Jibun address
  String roadAddress;     // Road address
  String buildingName;    // Building name
  String zonecode;        // Zone code
  double? latitude;       // Latitude (from geocoding)
  double? longitude;      // Longitude (from geocoding)
  // ... and more fields
}
```

## 🌐 Web Support

The package automatically detects the platform and provides appropriate implementation:

- **Mobile**: Uses `InAppWebView` for embedded web content
- **Web**: Uses native DOM manipulation and JavaScript interop

No additional configuration needed - it just works! 🎉

## 🔧 Migration from kpostal

If you're migrating from the original `kpostal` package:

1. Update your `pubspec.yaml`:

   ```yaml
   dependencies:
     postal_ko: ^1.1.0 # Replace kpostal
   ```

2. Update imports:

   ```dart
   // Old
   import 'package:kpostal/kpostal.dart';

   // New
   import 'package:postal_ko/postal_ko.dart';
   ```

3. The API remains the same - no code changes needed! ✨

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Inspired by the original [kpostal](https://pub.dev/packages/kpostal) package
- Built with [Kakao Postcode Service](https://postcode.map.kakao.com/guide)
- Thanks to all contributors and users! 🎉
