# Micro Front-End

## Micro Front-end basic
* https://www.notion.so/webslaveship/Micro-Front-End-206ca51271bc4f6bbc5fded418201302#6ead5588ffb44797a50fa80c268b00f0

### MF의 기본 개념 및 구현 방법, 장단점.(ThoughtWorks 번역글)
[https://medium.com/@juyeon.kate/micro-frontends-번역글-1-5-29c80baf5df](https://medium.com/@juyeon.kate/micro-frontends-%EB%B2%88%EC%97%AD%EA%B8%80-1-5-29c80baf5df)
[https://medium.com/@juyeon.kate/micro-frontends-번역글-2-5-66e3a31b72a9](https://medium.com/@juyeon.kate/micro-frontends-%EB%B2%88%EC%97%AD%EA%B8%80-2-5-66e3a31b72a9)
[https://medium.com/@juyeon.kate/micro-frontends-번역글-3-5-ac4be12cf872](https://medium.com/@juyeon.kate/micro-frontends-%EB%B2%88%EC%97%AD%EA%B8%80-3-5-ac4be12cf872)
[https://medium.com/@juyeon.kate/micro-frontends-번역글-4-5-47cf7892b1d7](https://medium.com/@juyeon.kate/micro-frontends-%EB%B2%88%EC%97%AD%EA%B8%80-4-5-47cf7892b1d7)
[https://medium.com/@juyeon.kate/micro-frontends-번역글-5-5-e0b2c9028e93](https://medium.com/@juyeon.kate/micro-frontends-%EB%B2%88%EC%97%AD%EA%B8%80-5-5-e0b2c9028e93)

마이크로 프론트 엔드 역시 하나의 접근 방법이다. 해당 솔루션의 장점을 이해하고, 그에 들어 맞는 요구사항을 가진 환경에서 수행 되는지에 대한 검토도 필요하다.

"물론, 하나의 높은 수준의 아키텍처 결정(예 : “Micro Frontends를 만들어 보자”)이 코드 품질을 높여주는 것은 아닙니다. 우리는 어떤 경우에서든 코드에
대해 생각하고 품질에 노력을 기울이는 것을 피하면 안됩니다. (이는 늘 신경써서 잘 해야 하는 문제입니다.) 대신, 우리는 나쁜 결정을 어렵게 만들고,
좋은 결정을 쉽게 내리게 만들어서 성공으로 스스로를 유도합니다. 예를 들어, 제한된 컨텍스트 내에서는 도메인 모델을 공유하는 것이 어려워지므로 개발자는
자연스레 그렇게 할 가능성이 적어집니다. 이와 같이, Micro Frontends 는 어플리케이션의 여러 부분간에 데이터와 이벤트가
어떻게 전달되는지에 대해 명시하고, 숙고하도록 유도합니다. 이는 우리가 어쨌든 해야만 했던 것입니다." 👍

⇒ 이 문장에서 한번 더 생각해 볼 수 있는 바는 MF 역시 기존 아키텍처의 연장선상에 있다는 것이다.
그러나, 극단적인 차이라고 한다면, 빌드 도구를 완전히 다르게 사용할 수 있고, 심지어 gwt 같은 전혀 다른 환경의 통합도 가능하다.
즉 레거시 교체에 대해서는 완전히 자유로워 지고, 서로 다른 조직 간에도 같이 프로젝트를 진행 할 수도 있다.
그러나 앞서 말했듯, 높은 수준의 아키텍처 결정이 코드의 품질을 높여 주는 것이 아님을 경계해야 한다.
접근 방법 역시 MF 를 구현해 보기위해, 적당한 모델을 찾는 것이 아니라 ( 또한 우겨넣는 것이 아니라 ) 현재의 문제점을 살펴 보고,
그 문제의 여러 해결 대안에서 MF 가 탁월하다고 판단될 때, 선택되어야 할 것이다.

Q. 하나의 페이지가 있다고 하면, 어떻게 해당 페이지의 규격을 유지하고, 그 규격을 나타내고 공유할 것 인가?
예를 들어 A 페이지 하나의 페이지 조각에 조회 버튼이 있고 다른 조각에는 결과 화면이 있을 때, 조회 버튼 조각이 있는 페이지를 새로운 프로젝트로 교체할 때,
기존의 조회 버튼의 있음과 그 기능을 어떻게 가시적으로 표현 할 수 있는지.?
또는 극단적 하나의 페이지에 단 하나의 조각이 존재한다고 하면 그 페이지내 상세 스펙은 어떻게 표현할 것인지, 이런 것은 테스트 코드로서 커버할 수 있지만,
이것은 그 페이지 조각만이 아닌 교체되는 페이지에서도 동작해야 한다는 것,
예를 들어 이전 페이지 조각이 jest 로 작성되었다면, 결국 jest에 대한 의존성이 생기는 데 이런 것은 어떻게 극복할 것인지..

점진적인 업그레이드는 굉장히 큰 장점.
언제나 내가 코드를 쓰는 이순간에도 코드는 레거시가 되고, 시간이 지나면 더 나은 아키텍쳐와 솔루션 앞에서 너무 초라해 진다는 것.
그것을 교체 할 수 있다는 것은 큰 장점.

각 방법에 대해
방법 1. docker, aws 기술.. 그런데, 메인 템플릿이 유동적이라면,
방법 2. 이 접근 방식은 제품의 각 부분을 변경하기 위해 모든 micro frontends application을 다시 컴파일하고 릴리즈해야 함을 의미합니다 - 어느정도는 공감
방법 3. 보안 문제 때문이라도 힘들다.

스타일링
통합적인 해결책을 제시하는 방법은 없는가?
컨테이너 레벨에서 네임스페이스를 제공한다던가, 또는 충돌을 배포전에 검증한다던가??

공유 컴포넌트 라이브러리

가장 발생하기 쉬운 문제점 중 하나는, 이러한 컴포넌트를 너무 일찍, 너무 많이 만드는 것입니다.
~~ 이러한 이유로 우리는 팀이 초기에 일부 중복을 발생시키더라도 필요에 따라 코드베이스 내에 자체 컴포넌트를 만드는 것을 선호합니다.
공통된 패턴이 자연스럽게 나타나도록 하고, 컴포넌트의 API가 명확해지고 나면, 공유 라이브러리에서 중복 코드를 추출해낼 수 있고,
확실히 입증된 것들만을 가지고 있음을 확신할 수 있습니다.
⇒ 컴퍼넌트 확장은 방향성에 유의 해야 한다. 먼저 컴퍼넌트 스펙을 정하고, 개발하면 오버엔지니어링을 가져올수 있다.
빠르게 구현체를 만들고, 이후에 공통되는 요소의 발견이 필요하다. 지속적으로 발생하는 변경 사항과 코드에 변경 위치에 관심을 가지면,
올바른 리펙토링의 방향을 정할 수 있다.

⇒ dumb 컴퍼넌트가 제 1 대상 이다

⇒ ProductTable은 공유하면 안된다고 하지만, 지속적인 반복은 공유 대상이 된다. 다만, 확신을 가지기 까지 시간이 필요하다.

다른 극단에서는, 공유 라이브러리의 개발이 완전히 중앙집중화되면, 컴포넌트를 만드는 사람들과 이를 사용하는 사람들이 크게 단절될 것입니다.
우리가 본 최고의 모델은, 누구나 라이브러리에 기여할 수 있지만 품질, 일관성, 유효성을 보장할 책임이 있는 담당자(해당 개인 또는 팀)가 있는 것입니다.
공유 라이브러리를 유지 관리하는 일은 수준높은 기술력을 필요로 하지만, 또한 많은 팀들 간의 협업을 수행하는 데 필요한 인적 기술도 필요로 합니다.👍

### impl 
#### 구현 방법들
https://itnext.io/11-micro-frontends-frameworks-you-should-know-b66913b9cd20
https://www.notion.so/webslaveship/Micro-Front-End-206ca51271bc4f6bbc5fded418201302#3b2b3ec67a424823a67328db84a91435

##### troubleshooting
https://www.notion.so/webslaveship/Micro-Front-End-206ca51271bc4f6bbc5fded418201302#e291a886d55f4588a0f6d6d2fab4fb26

⇒ 컴파일러 변경 react@1.0.2
⇒ bit 사이트에서는 색상이 변한다???
https://www.notion.so/webslaveship/Micro-Front-End-206ca51271bc4f6bbc5fded418201302#f0363f38a39f45e7977163d86c3f8dc0

#### bit - nextjs
https://www.notion.so/webslaveship/Micro-Front-End-206ca51271bc4f6bbc5fded418201302#b67875764b2e46919358094f03076df4

#### build 통합
https://bit.dev/
https://www.notion.so/webslaveship/Micro-Front-End-206ca51271bc4f6bbc5fded418201302#eead5b058a024367816a5407018cff56

#### run time 통합
https://www.notion.so/webslaveship/Micro-Front-End-206ca51271bc4f6bbc5fded418201302#29f058b6c5364ed8989cc0cbd3773ebc
https://medium.com/@ScriptedAlchemy/micro-fe-architecture-webpack-5-module-federation-and-custom-startup-code-9cb3fcd066c

## 생각해보아야 할것들
### 충돌
#### Css
[How to Share React Components Between NextJS Projects](https://blog.bitsrc.io/how-to-share-react-components-between-nextjs-projects-c0857bbc1fcb)

#### JS 검증

#### 충돌 검증

### communication
https://www.notion.so/webslaveship/Micro-Front-End-206ca51271bc4f6bbc5fded418201302#2416e4ed975c4427aa13e64eab7fa5d8

### 분리와 확장 및 composition

### 규약 및 체계 공유
=> 최소화 해야 한다. 도메인 로직 공유는 피하고, 만약 그래야 한다면, 하나의 페이지 통합하는 것이 맞는지 검토 필요.
=> mf app이 mf app을 가지는 경우도 있지 않을까?






