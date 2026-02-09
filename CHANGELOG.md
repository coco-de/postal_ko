## 1.1.0

### 🔄 MIGRATION - Kakao Postcode Domain & Namespace Update

카카오 우편번호 서비스의 도메인 및 API 네임스페이스 변경에 대응합니다.
([참고: daumPostcode/QnA#1498](https://github.com/daumPostcode/QnA/issues/1498))

- **CDN 도메인 변경**: `t1.daumcdn.net` → `t1.kakaocdn.net`
- **JS API 네임스페이스 변경**: `daum.Postcode` → `kakao.Postcode`
- **서비스 도메인 참조 업데이트**: `postcode.map.daum.net` → `postcode.map.kakao.com`

### 🐛 BUG FIXES

- 로컬 서버 경로 버그 수정: `/packages/kpostal/assets/` → `/packages/postal_ko/assets/`
- LICENSE 파일 내 Git merge conflict markers 제거
- CHANGELOG 내 패키지명 오타 수정 (`cocode_postal` → `postal_ko`)

### 📝 DOCUMENTATION

- README.md / README.ko-kr.md 서비스 도메인 링크 업데이트
- README.ko-kr.md 패키지명 및 import 경로를 `postal_ko`로 통일

## 1.0.0

### 🚀 NEW FEATURES

- **Cross-platform support**: Now supports both mobile (iOS/Android) and web platforms seamlessly
- **Web integration**: Native web support using Kakao Postcode Service with DOM manipulation
- **Unified API**: Single package that works across all platforms without separate web dependencies

### 🔧 TECHNICAL IMPROVEMENTS

- **Modern web interop**: Uses `dart:js_interop` and `package:web` for robust web integration
- **Conditional imports**: Platform-specific code loading to prevent build errors
- **Memory leak prevention**: Proper cleanup of DOM elements and event listeners
- **Error handling**: Robust null-safe JSON parsing and widget lifecycle management
- **Performance optimization**: Removed unnecessary debug logs and optimized resource usage

### 🛠️ DEPENDENCIES

- Updated minimum supported SDK version to Flutter 3.24/Dart 3.5
- Updated `flutter_inappwebview` dependency to `^6.1.5`
- Added `web: ^1.1.0` for modern web support
- Updated `geocoding` to `^3.0.0`

### 📱 COMPATIBILITY

- **Mobile**: Full backward compatibility with existing mobile implementations
- **Web**: New web support with identical functionality to mobile version
- **Cross-platform**: Seamless experience across all supported platforms

### 💥 BREAKING CHANGES

- Package name changed from `kpostal` to `postal_ko`
- Minimum Flutter version: `3.24.0`
- Minimum Dart SDK version: `^3.5.0`
- Updated Android `minSdkVersion` to `19`
- The minimum iOS version: `9.0` with `XCode version >= 14`

## 0.5.1

- fix #12 issue : show representative jibunAddress

## 0.5.0

- remove pubspec.lock from git.
- update dependencies.
- improve method for searching latitude and logitude through geocoding.
  if not found by eng address, retry using kor address.
- log info.

## 0.4.2

- fix a bug below Android 10.

## 0.4.1

- add "bname1" parameter.

## 0.4.0

- remove "webview_flutter" from dependencies.
  all components related to Webview(local hosting, javascript message, view page...) are integrated using "flutter_inappwebview" package.

## 0.3.2

- fix "not callback when geocoding value is null"
- fix protocol error and update html file

## 0.3.1

- fix platform geocoding returns wrong coordinates.
- add kakao geocoding(optional)
- update docs

## 0.3.0

- provides latitude and logitude
- update docs

## 0.2.0

- add search w/ localhost server

## 0.1.3

- update README.md
- add Korean docs
- add 'userSelectedAddress' getter

## 0.1.2

- update docs typo

## 0.1.1

- update docs & fix android bug(can't listen callback)

## 0.1.0

- initial publish
