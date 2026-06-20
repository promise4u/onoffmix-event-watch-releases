# ONOFFMIX Event Watch — Releases

발표 운영을 위한 크로스 플랫폼 타이머. Mac · iPhone · iPad · Apple Watch 가 손목까지 같은 시간으로 동기화됩니다.

> 이 저장소는 **macOS 데스크탑 앱(.dmg)의 공개 배포 채널**입니다.
> 코드 저장소가 아닙니다 — 빌드 산출물만 올립니다.
> 제품 페이지 → [onoffmix.com/apps/event-watch](https://onoffmix.com/apps/event-watch)
>
> iPhone · iPad · Apple Watch 는 App Store 에서 받습니다 →
> [apps.apple.com/us/app/onoffmix-event-watch/id6779810502](https://apps.apple.com/us/app/onoffmix-event-watch/id6779810502)

---

## 다운로드 (macOS)

### 안정 URL (최신 버전 자동 연결)

```
https://github.com/promise4u/onoffmix-event-watch-releases/releases/latest/download/ONOFFMIX-Event-Watch.dmg
```

위 URL은 항상 최신 안정 버전을 가리킵니다. 새 버전이 나오면 별도 안내 없이 자동으로 갱신됩니다.

### 시스템 요구사항

- macOS 12 (Monterey) 이상
- Apple Silicon (M1/M2/M3/M4) 또는 Intel (Universal binary)
- 동기화 기능을 사용하려면 Wi-Fi 또는 외부망 (Cloudflare relay 자동 폴백)

### 첫 실행

1. DMG 다운로드 → 더블클릭으로 마운트
2. `ONOFFMIX.COM Event Watch.app` 아이콘을 **Applications** 폴더로 드래그
3. Launchpad 또는 Spotlight 에서 **Event Watch** 실행
4. 첫 실행 시 macOS Gatekeeper 가 "확인되지 않은 개발자" 경고를 띄울 수 있습니다.
   - Apple Developer ID 로 서명 + 공증(notarize) 처리된 빌드이지만, Safari 가 아닌 다른 브라우저로 다운로드한 경우 경고가 표시됩니다.
   - **해결**: Finder 에서 앱을 우클릭 → **열기** → 대화상자에서 **열기** 확인. 한 번만 통과하면 이후 일반 실행 가능.

### 무결성 확인 (선택)

DMG 와 함께 `.sha256` 파일이 배포됩니다.

```bash
shasum -a 256 ONOFFMIX-Event-Watch.dmg
# 결과를 ONOFFMIX-Event-Watch.dmg.sha256 의 해시와 비교
```

해시가 일치하지 않으면 다운로드 손상 또는 변조 — 재다운로드 권장.

---

## 다운로드 (iOS · iPadOS · watchOS)

iPhone · iPad · Apple Watch 용 Universal 앱은 **Apple App Store** 에서 무료로 받을 수 있습니다.

**App Store 링크** → [apps.apple.com/us/app/onoffmix-event-watch/id6779810502](https://apps.apple.com/us/app/onoffmix-event-watch/id6779810502)

### 시스템 요구사항

- **iPhone / iPad** — iOS 17 / iPadOS 17 이상
- **Apple Watch** — watchOS 10 이상 (paired iPhone 필요)
- 자동 동기화 — 같은 Wi-Fi 의 Mac 데스크탑 앱과 mDNS 자동 발견, 다른 망에서는 Cloudflare relay 자동 폴백

### 디바이스별 설치

| 디바이스 | 설치 경로 |
|---|---|
| iPhone | App Store → 검색 "ONOFFMIX Event Watch" → 받기 |
| iPad | 위와 동일 (Universal 앱 — 자동 iPad 레이아웃) |
| Apple Watch | iPhone 에 설치된 후 watch app 에서 자동 설치 권유 알림 — 페어링된 워치에 설치 |

### 첫 실행 (iPhone 기준)

1. App Store 에서 받기 → 홈 화면에서 **이벤트 워치** 탭
2. 첫 launch 시 모드 자동 감지:
   - 같은 Wi-Fi 에 Mac sync 호스트가 있으면 → **Bridge 모드** (Mac 시간 그대로 미러)
   - 없으면 → **Standalone 모드** (휴대폰 자체가 timer source)
3. Apple Watch 가 페어링되어 있으면 자동으로 손목까지 시간 흐릅니다.

---

## 제품 개요

**메모러블 씽**: 발표자가 어디에 있든, 어떤 디바이스든, 시간이 정확히 손에 있습니다.

| 디바이스 | 역할 |
|---|---|
| **Mac** | Source of truth. WebSocket 호스트 + 운영자 컨트롤. |
| **iPad** | 운영자 컨트롤 보조 또는 발표자 무대 시계. |
| **iPhone** | Mac 의 미러 또는 단독 Standalone 모드. |
| **Apple Watch** | 손목 위 미러. WKExtendedRuntimeSession 으로 1시간 이상 표시 유지. |

### 핵심 기능

- **Drift-free wall-clock 타이머** — 30분 발표에서도 1초 이하 오차
- **다중 모드** — 스톱워치 · 카운트다운 · 발표(Talk + Q&A 분리)
- **자동 동기화** — 같은 Wi-Fi 면 mDNS 로 자동 발견, 다른 망이면 Cloudflare relay 폴백
- **12 종 milestone alert sound** — Web Audio 합성, sample-free
- **6 locale** — 한국어 · 영어 · 일본어 · 중국어 (간체) · 독일어 · 프랑스어
- **Q&A 시간 자동 균형** — 발표 일찍 끝나면 Q&A 늘어남, 초과하면 줄어듦

iOS 디바이스 (iPhone · iPad · Apple Watch) 는 **[App Store](https://apps.apple.com/us/app/onoffmix-event-watch/id6779810502)** 에서 무료로 받을 수 있습니다 — 같은 sync 레이어로 자동 페어링.

---

## 라이선스

DMG 배포물 자체는 ONOFFMIX 의 사용자 라이선스 조건을 따릅니다.
이 저장소(README + LICENSE)는 MIT 라이선스 — 배포 채널 메타데이터에만 적용.

---

## 문의 / 버그 리포트

- 제품 페이지: [onoffmix.com/apps/event-watch](https://onoffmix.com/apps/event-watch)
- 이메일: dev@onoffmix.com

---

*이 저장소는 빌드 산출물만 호스팅합니다. 소스 코드는 비공개입니다.*
