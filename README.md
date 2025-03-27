# 🚀 Advanced Web Navigation (map) 🚀

Leaflet.js 기반의 고급 웹 내비게이션 데모 애플리케이션입니다. 글래스모피즘 UI, 다양한 입력 방식(텍스트, 지도 클릭, 음성), 경로 유형 및 지도 스타일 선택 기능을 제공하며, **별도의 API 키 없이** (Daum 우편번호 서비스, OpenStreetMap Nominatim/OSRM 데모 서버 활용) 기본적인 주소 검색 및 경로 탐색 기능을 구현한 예제입니다.

**[주의]** 이 프로젝트는 데모 및 학습 목적으로 제작되었으며, 사용된 외부 API(Nominatim, OSRM 데imo 서버)의 제약 조건으로 인해 **상업적 용도나 실제 서비스에는 적합하지 않습니다.**

## ✨ 주요 기능

*   **🗺️ 인터랙티브 지도**: Leaflet.js를 사용한 지도 표시 및 상호작용.
*   **💎 글래스모피즘 UI**: 반투명하고 세련된 사용자 인터페이스 디자인.
*   **⌨️ 다양한 입력**:
    *   **텍스트 검색**: Daum 우편번호 서비스를 이용한 출발지/목적지 주소 검색.
    *   **지도 클릭**: 지도를 직접 클릭하여 출발지/목적지 설정.
    *   **현재 위치**: 버튼 클릭으로 현재 위치 자동 출발지 설정 (브라우저 Geolocation API).
    *   **🎤 음성 입력**: Web Speech API를 이용해 음성으로 목적지를 입력하고 현재 위치에서 즉시 경로 탐색 시작.
*   **📍 주소-좌표 변환**: Daum 우편번호 서비스 결과(주소)를 OpenStreetMap Nominatim API를 통해 위도/경도 좌표로 변환 (**API 키 불필요**, 사용량 제한 및 정확도 이슈 있음).
*   **🚗 경로 탐색 및 표시**: OSRM (Open Source Routing Machine) 데모 서버를 이용하여 선택된 프로필(자동차, 도보, 자전거)에 따른 경로 탐색 및 지도 위 표시 (Leaflet Routing Machine 활용).
*   **🎨 지도 스타일 선택**: 다양한 무료 타일 레이어(기본, 위성, 다크 모드 등) 선택 가능.
*   **🗣️ 음성 안내 (TTS)**: Web Speech API를 사용하여 주요 상태 변경 및 경로 안내 시 간단한 음성 피드백 제공.
*   **⚙️ UI 컨트롤**: 컨트롤 패널 숨기기/보이기 토글 기능.

## 🖼️ 데모 (스크린샷/GIF 추가 권장)

*(이곳에 애플리케이션의 스크린샷이나 작동 GIF를 추가하면 좋습니다.)*
`![Demo Screenshot](images/demo.png)` <!-- 예시: images 폴더에 demo.png 추가 -->

## 🛠️ 기술 스택

*   HTML
*   CSS (Tailwind CSS - CDN 방식)
*   JavaScript
*   [Leaflet.js](https://leafletjs.com/) - 인터랙티브 지도 라이브러리
*   [Leaflet Routing Machine](https://www.liedman.net/leaflet-routing-machine/) - 경로 탐색 플러그인
*   [Daum 우편번호 서비스](https://postcode.map.daum.net/guide) - 주소 검색 UI 제공 (API 키 불필요)
*   [OpenStreetMap Nominatim](https://nominatim.org/) - 주소-좌표 변환 (Geocoding) API (API 키 불필요, **사용량 제한 엄격**)
*   [OSRM Demo Server](http://project-osrm.org/) - 경로 계산 API (**데모용 서버**, 사용량 제한 및 불안정성)
*   [Web Speech API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Speech_API) (Speech Recognition & Synthesis) - 음성 인식 및 TTS
*   [Browser Geolocation API](https://developer.mozilla.org/en-US/docs/Web/API/Geolocation_API) - 현재 위치

## ⚙️ 설정 및 사용법

1.  **저장소 복제 또는 다운로드**:
    ```bash
    git clone https://github.com/hwkims/map.git
    cd map
    ```
    또는 ZIP 파일 다운로드 후 압축 해제.

2.  **로컬 웹 서버 실행**:
    ⚠️ **중요**: 보안 정책으로 인해 `file://` 경로에서 직접 HTML 파일을 열면 API(Daum Postcode, Geolocation, Speech 등)가 정상적으로 작동하지 않거나 오류가 발생할 수 있습니다. 반드시 로컬 웹 서버를 사용하여 실행하세요.

    *   **VS Code 사용자**: [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) 확장 프로그램 설치 후, HTML 파일 우클릭 > `Open with Live Server` 선택.
    *   **Python 3 사용자**: 프로젝트 폴더 내 터미널에서 `python -m http.server` 실행 후 브라우저에서 `http://localhost:8000` (또는 지정된 포트) 접속.
    *   **Python 2 사용자**: `python -m SimpleHTTPServer` 실행.
    *   **Node.js 사용자**: `npm install -g http-server` 설치 후 `http-server .` 실행.

3.  **브라우저에서 접속**: 웹 서버가 실행된 주소(예: `http://localhost:8000/your_html_file.html`)로 접속합니다.

4.  **(선택) 마이크 권한 허용**: 음성 입력 기능을 사용하려면 브라우저의 마이크 접근 권한 요청 시 '허용'을 선택해야 합니다.

## ⚠️ 중요 참고 및 제한 사항

*   **Nominatim 사용 정책**: OpenStreetMap Nominatim은 무료 공개 서비스이지만, **매우 엄격한 사용량 제한 정책**(IP당 초당 1회 미만 요청 권장)이 있습니다. 과도한 사용 시 **IP가 차단**될 수 있으며, 상업적/대규모 서비스에는 절대 사용해서는 안 됩니다. 또한, 국내 상세 주소(신축 건물, 아파트 동/호수 등)에 대한 **좌표 정확도가 낮을 수 있습니다.**
    *   [Nominatim Usage Policy](https://operations.osmfoundation.org/policies/nominatim/)
*   **OSRM 데모 서버 정책**: 경로 계산에 사용되는 OSRM 데모 서버는 테스트 및 데모 목적으로만 제공되며, **실제 서비스 용도로는 부적합**합니다. 사용량 제한이 있고 서버가 불안정하거나 예고 없이 중단될 수 있습니다. 실제 서비스에는 자체 OSRM 서버를 구축하거나 유료 라우팅 서비스를 이용해야 합니다.
    *   [OSRM API Usage Policy](https://github.com/Project-OSRM/osrm-backend/wiki/Api-usage-policy)
*   **Daum 우편번호 서비스**: API 키 없이 무료로 사용 가능하지만, 서비스 약관(하단 로고 표시 유지, 스크립트 임의 수정 금지 등)을 준수해야 합니다.
*   **Tailwind CSS CDN**: 현재 데모를 위해 CDN 방식을 사용했으나, 실제 프로덕션 환경에서는 Tailwind CSS를 빌드 과정(PostCSS 플러그인 또는 Tailwind CLI 사용)에 포함하는 것이 좋습니다.
*   **Web Speech API 브라우저 호환성**: 음성 인식 및 TTS 기능은 브라우저별로 지원 수준과 성능이 다를 수 있습니다. Chrome, Edge 등 최신 브라우저에서 가장 잘 작동하는 경향이 있습니다.
*   **API 키 불필요**: 위 제약사항에도 불구하고, 이 프로젝트는 Kakao/Naver/Google 등 별도 **API 키 발급 없이** 핵심 기능을 구현했다는 점에서 의의를 가집니다.

## 💡 향후 개선 아이디어

*   보다 안정적인 지오코딩/라우팅 API 연동 (자체 서버 구축 또는 유료 API 사용).
*   Tailwind CSS 빌드 프로세스 도입.
*   상세 경로 안내 UI/UX 개선 (턴바이턴 정보 표시 등).
*   사용자 설정 저장 (지도 스타일, 경로 프로필 등).
*   경로 저장 및 불러오기 기능.
*   오류 처리 로직 고도화.

## 📜 라이선스

이 프로젝트는 [MIT 라이선스](LICENSE) 하에 배포됩니다. (저장소에 LICENSE 파일을 추가하는 것을 권장합니다.)
