# 🧾 달라 안드로이드 개발 규칙

## 🎨 아키텍처 패턴 및 디자인 패턴

- 본 프로젝트는 `MVVM` 아키텍처와 `Layer` 아키텍처로 구성되어있습니다.
- `REST-Ful API` 호출 결과는 공통적으로 sealed 클래스를 활용한 `State` 패턴 및 `UseCase` 패턴을 사용합니다.

## 👨‍💻 코드 규칙

- 🧹 사용하지 않는 import는 지워주세요!
    - Ctrl + Alt + O 누르면 자동 정리됩니다.
- 📛 변수의 네이밍은 명확하게 적어주세요!
- 📃 본인이 작성한 클래스 위에 주석(doc)을 달아주세요!
    - https://kotlinlang.org/docs/kotlin-doc.html#block-tags
    - [번역] https://runebook.dev/ko/docs/kotlin/docs/reference/kotlin-doc
- 🙅 데이터 바인딩 사용을 지양해주세요.
- 🐫 xml의 id는 `camelCase`로 작성해주세요!
    - View(A&F) 계층에서 `ViewBinding`으로 사용할때 `snake_case`보다 코드 추적이 몇배는 좋습니다.
- 🐪 data class의 프로퍼티는 `camelCase`로 작성해주세요!
    - 서버에서 `snake_case`로 보낼경우 아래와 같이 해결해주세요.
        - ```
            data class MainPageData(
                @SerializedName("center_banner")
                val eventBanner: List<EventBannerData>
            )
            ```
- 🔍 A&F(액티비티/프래그먼트)에서 `LiveData` 및 `StateFlow`를 관찰하는 함수는 `observe{PublisherName}()`, `collect{PublisherName}()` 와 같은 형식으로 작성해주세요.
    - `observeViewModel()` : 뷰 모델의 `LiveData`를 관찰
    - `collectViewModel()` : 뷰 모델의 `StateFlow`를 수집
    - `collectEvent()` : 이벤트 버스의 `StateFlow` 수집
    - `collectLiveManager()` : 방송방 매니저의 `StateFlow` 수집
    - 접근 제한자는 필수로 작성해주세요.(public 은 안해줘도 됩니다.)

## 📦 배포 규칙

- 🏪 앱 버전은 `Release`.`Major`.`Minor` 로 소규모 업데이트는 `Minor`, 중-대규모 업데이트는 `Major` 버전을 그 외, `Release` 는 마켓에 따라 변경될 수 있습니다.
    - `PlayStore` 1.x.x
    - `OneStore` 2.x.x
- ⏳ 심사제출은 항상 최신 `origin & develop` 브랜치입니다.
- 🥳 심사가 완료됐을때, 앱을 출시한 후에 `origin & master` 버전을 푸시해주세요.
