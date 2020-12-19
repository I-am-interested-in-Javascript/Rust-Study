# Installation

Rust 를 설치해보자. `rustup`(Rust 버전과 관련 툴을 관리하는 command line tool)을 통해서 rust를 설치하자. 다운로드를 위해서 인터넷을 연결을 확인하세요. 

* Note: `rustup`을 무슨 이유에선가 쓰기 싫다면, [Rust 설치 페이지](https://www.rust-lang.org/tools/install)를 읽어보세요

다음은 latest stable rust compiler 버전을 설치하는 단계이다. Rust의 안정성(stability)는 이 책의 모든 예제들이 더 최신의 Rust버전으로도 문제없이 컴파일 되는것을 보장한다. Rust 버전마다 출력 결과는 조금 다를수도 있다. 이건 Rust가 에러메시지나 경고 메시지를 조금씩 개선하기 때문이다. 즉, 다른 최신 stable rust 버전을 이용하면 책의 예제는 잘 동작할 것이다. 

* Command Line Notation
    - 이 챕터와 책전반에 걸쳐, 터미널에서 쓰는 명령어들을 보여줄것이다. `$`로 시작하는 라인들은 터미널에 입력하는 명령어들이다. `$`는 입력안해도 된다; 이건 그냥 명령어가 시작되는걸 표시하는 것이다. `$`로 시작하지 않는 것들은 주로 이전 명령의 결과를 보여주는 것이다. 추가적으로 Window Powershell 에만 해당하는 명령은 `>`로 시작한다. 


## Linux 나 macOS에서 rustup 설치하기

Linux나 mac의 경우, 터미널을 열고 아래의 명령어를 입력해라

`$ curl --proto '=https' --tlsv1.2 https://sh.rustup.rs -sSf | sh`

위의 명령은 스크립트를 다운로드 받고, latest stable version의 `rustup` 설치를 시작한다. password를 입력하라는 창이 뜰수도 있다. 만약 설치가 성공적이라면 아래 결과가 뜰것이다. 

`Rust is installed now. Great!`

추가적으로 linker가 필요하다. 이미 설치되어있을 가능성이 높지만, rust 프로그램을 컴파일하려고 할때 `linker could not execute`라는 에러가 뜨면 linker가 설치되어있지 않다는 것이다. 이 경우에는 수동으로 linker를 설치해야한다. C 컴파일러가 알맞은 linker랑 같이 설치 되기때문에 c 컴파일러를 설치해라. 또한, 어떤 rust 패키지는 c 코드 기반이라 c compiler가 필요하다. 그러니까, 지금 설치하는게 좋다. 


## updating and uninstalling

`rustup`을 통해서 rust를 설치하고나면 최신 버전으로 업데이트하는 것은 쉽다. 아래의 명령어를 입력하면 rust 업데이트를 할 수 있다. 

`$ rustup update`

rust랑 `rustup`을 삭제 하고 싶으면 아래 uninstall 스크립트를 실행해라

`$ rustup self uninstall`

## troubleshooting

rust가 제대로 설치 되어잇는지 확인하기 위해서 아래 라인을 입력해라

`$ rustc --version`

latest stable version의 버전 넘버, 커밋 해쉬, 그리고 커밋 날짜를 볼 수 있어야한다. 

`rustc x.y.z (abcabcabc yyyy-mm-dd)`

이렇게 잘뜨면 rust가 잘 설치 됬다는 것이다. 만약 이게 안보이고 윈도우면 `%PATH%` 시스템 변수에 rust가 있는 지 확인해라. 만약 이게 잘 되있고, rust가 제대로 동작하고 있지 않으면 원인을 파악할 수 있는 다양한 곳이 있다. 

가장 쉬운 곳은 [공식 rust 디스코드](https://discord.com/invite/rust-lang) 의 #beginners 채널이다.  여기서 Rustaceans (a silly nickname we call ourselves) 들과 채팅할수 있고, 이사람들이 잘 도와줄것이다. 다른 [유저 포럼](https://users.rust-lang.org/) 이나 [스택오버플로우](https://stackoverflow.com/questions/tagged/rust) 에도 많은 자료들이 있다. 


## Local documentation
Rust를 설치하면 Rust 문서도 같이 설치된다. 그래서 오프라인에서 공식 문서도 읽을 수 있다. `rustup doc`를 입력하면 브라우저에서 docs를 읽을 수 있다. 

스탠다드 라이브러리가 제공하는 타입이나 함수를 사용할때 긴가민가하면 api documentation을 통해서 자료를 찾아라!


[출처](https://doc.rust-lang.org/book/ch01-01-installation.html)

