# Ionic
<img width="700" alt="Untitled" src="https://github.com/kihyuni1207/ionic_study/assets/127191624/7dab73cb-4de3-451e-9064-4ed9ad497fa9">

## 내가 Frontend 개발자라면  웹 앱 둘다 알아야 한다

- 모바일 앱이 새로운 비즈니스 기회를 열어줄 창구로 부상, 많은 기업들이 어플로 만들고 있는 추세이다….
- 아직도 시장은 웹이 좀더 우세하지만 Front개발자라면 둘다 할줄 알아야 한다…
- 앱 개발의 방식은 크게 네이티브 앱, 모바일 웹 앱, 하이브리드 앱과 같이 3가지로 나뉘는데 각각의 요소들을 따져보겠슴다

## 앱 3가지!

### 기기에 최적화된 기능을 구현할 수 있는, 네이티브 앱(Native APP)

- ‘네이티브 앱(Native APP)’이란 모바일 기기에 최적화된 네이티브 언어로 개발된 앱을 뜻합니다. 국가별로 언어가 다르듯, 모바일 운영체제도 개발을 위해 각기 다른 언어를 사용해야 합니다. 안드로이드 운영체제의 대표적인 네이티브 언어는 코틀린(Kotlin) 또는 자바(Java)이며, iOS는 스위프트(Swift) 또는 오브젝티브 C(Objective C)이죠. 해당 언어를 기반으로 각 모바일의 운영체제에 딱 맞는 앱을 개발하면 그것이 네이티브 앱입니다.

<img width="700" alt="Untitled2" src="https://github.com/kihyuni1207/ionic_study/assets/127191624/77d4a217-71d9-4117-8c2f-dcd667d90739">

- 예를들어 네이티브 앱은~

<img width="700" alt="Untitled3" src="https://github.com/kihyuni1207/ionic_study/assets/127191624/b92984b9-5916-41e0-a170-ad7f20518d25">

### 비용이 저렴하고, 업데이트가 쉬운, 모바일 웹 앱(Web APP)

- 네이티브 앱처럼 보이고, 기능 또한 앱과 동일하게 구현되지만, 웹 기술을 활용하여 만들어진 앱을 ‘웹 앱(Wed APP)’이라고 합니다. 네이티브 앱과 달리 웹 앱은 웹 기반의 HTML, CSS, Javascript 등을 활용하며, 별도의 앱 파일을 설치하지 않고 인터넷 브라우저를 기반으로 작동됩니다.

<img width="700" alt="Untitled4" src="https://github.com/kihyuni1207/ionic_study/assets/127191624/17acae33-857c-4020-b9cc-7d004c78e5df">

- 예를들어 모바일 웹 앱은~

<img width="700" alt="Untitled5" src="https://github.com/kihyuni1207/ionic_study/assets/127191624/25ec2e8f-2b63-4466-8736-6127f3f95758">

### 하이브리드 앱(**Hybrid** APP)

- ‘하이브리드 앱(Hybrid APP)’은 네이티브 앱과 웹 앱의 개발 방식을 모두 사용합니다. 앱의 화면이나 기능 등 콘텐츠 영역은 웹 기반으로 제작하고 겉모습은 앱 마켓 등록과 설치를 위해 네이티브 앱으로 포장한 것이죠. 두 가지 개발 방식을 이용하므로 웹과 앱의 API를 모두 사용할 수 있습니다. 따라서 웹 앱에서는 불가능 했던 디바이스 자체 기능에 접근할 수 있습니다.

<img width="700" alt="Untitled6" src="https://github.com/kihyuni1207/ionic_study/assets/127191624/8a94c00c-b51b-43b7-b7ab-91be526c6213">

- 예를들어 하이브리드 앱은~

<img width="700" alt="Untitled7" src="https://github.com/kihyuni1207/ionic_study/assets/127191624/5c8965cd-654a-4f95-ae64-5aa9ad7a8ce1">

### 3가지 앱의 대한 비교 및 자료 출저

<img width="700" alt="Untitled8" src="https://github.com/kihyuni1207/ionic_study/assets/127191624/e43e8e98-e0ed-4ddf-bccd-2eabdfa6a6a8">

- 자료 출처
    - https://blog.hectodata.co.kr/app_kinds/

## 하이브리드 개발 프레임워크 Ionic!

![Untitled9](https://github.com/kihyuni1207/ionic_study/assets/127191624/701e1f93-8fa0-40ac-891d-86bb5a78b934)

### 하이브리드 앱 개발 프레임워크, ‘아이오닉 프레임워크(Ionic Framework)’

- 아이오닉은 하이브리드 모바일 앱 개발을 위해 만들어진 HTML5 프레임워크 입니다. 하이브리드 앱은 네이티브 앱에 비해서 보다 다양할 플랫폼을 지원하며, 서드파티(third party) 코드를 이용할 수 있습니다..
- 스마트폰에 최적화된 ui를 디자인할 수 있으며, 무엇보다 크로스 플랫폼 개발이 가능하며 HTML5의 부족한 API를 네이티브 API로 보완할 수 있다.
- 주로 TypeScript언어를 이용하고 Angular, Vue, React를 통해 하나의 코드로 android/ios/web을 동시에 시작할 수 있는 크로스 플랫폼 장점이 있다. ( 단 웹 앱 둘다 적용하기 위해선 css 설정을 굉장히 잘해야한다… )

### ‘아이오닉 프레임워크(Ionic Framework) 왜 써야 하는가?’

- [일단] 네이버 클라우드 플랫폼에서 하이브리드 아이오닉 프레임워크를 선택
- ionic framework 기반으로 작업

<img width="700" alt="Untitled10" src="https://github.com/kihyuni1207/ionic_study/assets/127191624/eaaef3f4-f497-44e7-b1e0-d6f2d8ba4505">

- 네이버 클라우드 플랫폼에서 ionic을 선택한 이유? 가장 강점으로는 일단 하이브리드! 대부분 웹 개발 경험을 가진 개발자를 더 만나기 쉽고 웹 베이스 프로그래밍 기술을 활용하면서도 크로스 플랫폼 적용 관점에서 볼때 하이브리드 앱 개발 방식이 매우 유리하다고 생각했다고 합니다 네이버가
- 사진을 으로 보면 하이브리드 앱은 모든걸 전부 호환해 준다 대박

<img width="700" alt="Untitled11" src="https://github.com/kihyuni1207/ionic_study/assets/127191624/80b44acf-9b35-4833-a50c-28716e858912">

### ‘아이오닉 프레임워크(Ionic Framework) 장점’

- 무료 오픈 소스
    - 공식 홈페이지에 들어가면 누구나 쉽게 설치 가능하며 오픈 소스를 제공한다
    - 링크 https://ionicframework.com/
- 수많은 UI 구성요소 제공

<img width="700" alt="Untitled12" src="https://github.com/kihyuni1207/ionic_study/assets/127191624/2efff1ae-5651-4382-8cf2-9e763491b682">

- 크로스 플랫폼 빌드
    - iOS, 안드로이드 뿐만 아니라 다양한 플랫폼을 지원한다, 한 번 코드를 작성하면 별다른 수정 없이도 다른 플랫폼으로 빌드가 가능 최대 장점

<img width="700" alt="Untitled13" src="https://github.com/kihyuni1207/ionic_study/assets/127191624/0b46413a-70bd-4a9c-a0ff-eb96a3bee729">

### 이제 만들어 보자..
### 🍏로직은 올려놓았으니 확인해보세요~ </span>

### Ionic + vue3 개발 진행

- Front 환경 구성
    - node 버전 : 16.20.2
    - Java 버전: 11.0.18
    - vue 버전 : 3.12.1
    - ionic 버전 7.1.1
    - nvm 버전 : 0.39.0
    - yarn 버전 : 1.22.19 → yarn berry 사용 x
    - npm 버전 : 8.19.4
    - 배포 : netlify → 네트리파이 사용

- 개발
    - 로그인
        - **`<ion-content>`**: Ionic 컨테이너로, 실제 콘텐츠와 로그인 폼을 포함
        - **`setup`** 함수 내에서 Vue 컴포넌트의 상태 및 로직을 설정한다.
        - **`ref`**를 사용하여 **`username`**, **`password`**, **`isLoading`**, **`showModal`**, 및 **`modalMessage`**와 같은 Vue 상태를 생성하고 초기화진행
        - **`login`** 함수는 사용자 이름과 비밀번호를 확인하여 **`isLoading`**을 사용하여 로딩 중임을 표시하며, 로그인이 성공하면 **`localStorage`**를 사용하여 로그인 정보를 저장하고 탭으로 tab1페이지로 화면 전환
    - 알람
        - 데이터는 브라우저의 로컬 스토리지 (localStorage)에 저장됩니다. 로컬 스토리지는 웹 애플리케이션에서 클라이언트 측 데이터를 저장하는 데 사용되는 브라우저 내부의 키-값 저장소예연
        - 여기서 **`localStorage.setItem('alarms', JSON.stringify(newAlarms));`** 코드 라인은 **`newAlarms`** 배열의 내용을 JSON 형식으로 직렬화하고 "alarms"라는 키로 로컬 스토리지에 저장함다
        - **`loadAlarms`** 함수가 페이지가 로드될 때 호출되며, 이 함수는 로컬 스토리지에서 "alarms" 키의 값을 읽어와 **`alarms`** ref에 할당하여 이전에 저장한 알람 데이터를 다시 불러오는 역할을 함다.

참고자료

- https://blog.naver.com/PostView.nhn?blogId=kncurationkorea&logNo=222265430039
- https://yozm.wishket.com/magazine/detail/295/
