# 매일 명언 앱 (Daily Quote App)

안드로이드 스튜디오를 사용한 명언 앱입니다.

## 주요 기능

### 1. 잠금화면 표시 ⭐
- **화면을 켤 때마다** 잠금화면에 오늘의 명언이 표시됩니다
- 화면이 꺼진 상태에서 켜지면 자동으로 명언이 나타납니다
- 잠금화면 알림에서 바로 다음 명언 보기, 공유 가능

### 2. 자동 업데이트
- 매일 자정(00:00)에 자동으로 새로운 명언으로 변경
- 앱 실행 시마다 오늘의 명언 표시
- 수동으로 다음 명언 보기 가능

### 3. 즐겨찾기
- 마음에 드는 명언을 저장
- 즐겨찾기 목록에서 언제든 확인 가능

### 4. 공유 기능
- SNS, 메시지로 명언 공유
- 잠금화면에서도 바로 공유 가능

### 5. 알림 기능
- 매일 원하는 시간에 새로운 명언 알림
- 시간 설정 가능

## 기술 스택

- **언어**: Kotlin
- **UI**: Jetpack Compose
- **데이터베이스**: Room Database
- **백그라운드 작업**: WorkManager, AlarmManager
- **저장소**: SharedPreferences
- **아키텍처**: MVVM

## 프로젝트 구조

```
DailyQuoteApp/
├── app/
│   ├── src/
│   │   └── main/
│   │       ├── java/com/example/dailyquote/
│   │       │   ├── data/
│   │       │   │   ├── local/
│   │       │   │   │   ├── QuoteDao.kt
│   │       │   │   │   └── QuoteDatabase.kt
│   │       │   │   ├── model/
│   │       │   │   │   └── Quote.kt
│   │       │   │   └── repository/
│   │       │   │       └── QuoteRepository.kt
│   │       │   ├── receiver/
│   │       │   │   ├── AlarmReceiver.kt
│   │       │   │   ├── BootReceiver.kt
│   │       │   │   └── ScreenOnReceiver.kt
│   │       │   ├── service/
│   │       │   │   └── LockScreenService.kt
│   │       │   ├── ui/
│   │       │   │   ├── navigation/
│   │       │   │   │   └── Navigation.kt
│   │       │   │   ├── screen/
│   │       │   │   │   ├── FavoritesScreen.kt
│   │       │   │   │   ├── HomeScreen.kt
│   │       │   │   │   └── SettingsScreen.kt
│   │       │   │   ├── theme/
│   │       │   │   │   ├── Color.kt
│   │       │   │   │   ├── Theme.kt
│   │       │   │   │   └── Type.kt
│   │       │   │   └── viewmodel/
│   │       │   │       └── QuoteViewModel.kt
│   │       │   ├── util/
│   │       │   │   ├── AlarmScheduler.kt
│   │       │   │   └── PreferencesManager.kt
│   │       │   ├── MainActivity.kt
│   │       │   └── QuoteApplication.kt
│   │       ├── res/
│   │       └── AndroidManifest.xml
│   └── build.gradle.kts
├── build.gradle.kts
└── settings.gradle.kts
```

## 설치 및 실행 방법

### 1. 안드로이드 스튜디오 설치
- [안드로이드 스튜디오](https://developer.android.com/studio) 최신 버전 다운로드 및 설치

### 2. 프로젝트 열기
```bash
1. Android Studio 실행
2. File > Open
3. DailyQuoteApp 폴더 선택
4. Gradle 동기화 대기
```

### 3. 앱 실행
```bash
1. 안드로이드 기기를 USB로 연결하거나 에뮬레이터 실행
2. Run 버튼(▶) 클릭 또는 Shift + F10
```

### 4. 권한 설정
앱 실행 후 다음 권한을 허용해주세요:
- **알림 권한** (Android 13+)
- **정확한 알람 권한** (Android 12+)

## 사용 방법

### 잠금화면에 명언 표시하기
1. 앱 실행 후 자동으로 잠금화면 서비스가 시작됩니다
2. 화면을 끄고 다시 켜면 잠금화면에 명언이 표시됩니다
3. 설정에서 잠금화면 표시 기능을 끄고 켤 수 있습니다

### 알림 설정하기
1. 설정 화면으로 이동
2. "매일 알림" 스위치 활성화
3. "알림 시간" 버튼을 눌러 원하는 시간 설정
4. 설정한 시간에 매일 새로운 명언 알림이 옵니다

### 즐겨찾기 사용하기
1. 홈 화면에서 하트 버튼을 눌러 현재 명언 저장
2. 상단의 하트 아이콘을 눌러 즐겨찾기 목록 확인
3. 즐겨찾기 목록에서 공유하거나 저장 해제 가능

### 명언 공유하기
1. 홈 화면 또는 즐겨찾기에서 공유 버튼 클릭
2. 원하는 앱(카카오톡, 문자, SNS 등) 선택
3. 명언이 자동으로 텍스트로 복사됩니다

## 주요 클래스 설명

### LockScreenService
- 잠금화면에 명언을 표시하는 포그라운드 서비스
- 화면이 켜질 때마다 명언을 업데이트하여 알림으로 표시

### ScreenOnReceiver
- 화면 켜짐 이벤트를 감지하는 BroadcastReceiver
- 화면이 켜지면 LockScreenService를 시작

### AlarmReceiver
- 매일 설정한 시간에 알람을 받는 BroadcastReceiver
- 새로운 명언으로 업데이트하고 알림 표시

### QuoteViewModel
- 명언 데이터와 UI 상태를 관리하는 ViewModel
- Room Database와 상호작용

## 문제 해결

### 잠금화면에 명언이 표시되지 않는 경우
1. 설정 > 앱 > 매일 명언 > 알림 권한 확인
2. 설정에서 "잠금화면 표시" 스위치가 켜져있는지 확인
3. 기기의 배터리 최적화 설정 확인 (일부 기기에서 백그라운드 서비스 제한)

### 알림이 오지 않는 경우
1. 설정 > 앱 > 매일 명언 > 알림 권한 확인
2. 정확한 알람 권한 확인 (Android 12+)
3. 배터리 최적화에서 앱 제외

### 앱이 백그라운드에서 종료되는 경우
일부 제조사(삼성, 샤오미 등)는 배터리 절약을 위해 백그라운드 앱을 적극적으로 종료합니다:
1. 설정 > 배터리 > 배터리 사용량 최적화
2. 매일 명언 앱을 "최적화하지 않음"으로 설정

## 향후 개발 계획

- [ ] 명언 카테고리 분류 (동기부여, 사랑, 성공 등)
- [ ] 사용자가 직접 명언 추가 기능
- [ ] 위젯 지원
- [ ] 다크 모드 테마
- [ ] 명언 폰트 및 배경 커스터마이징
- [ ] 외부 API 연동으로 더 많은 명언 제공

## 라이센스

이 프로젝트는 개인 학습 및 사용 목적으로 만들어졌습니다.

## 연락처

문의사항이 있으시면 이슈를 등록해주세요.
