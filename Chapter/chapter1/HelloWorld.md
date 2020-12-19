# Hello, World!

rust를 설치했으니, 첫 rust프로그램을 만들어보자. 새언어를 시작할때 `Hello, World!`를 출력하는 프로그램을 만드는 전통이 있다! 그래서 그거부터 할거다. 

* Note: 이책은 읽는 사람들이 command line에 대해서 기본적인 이해는 할거라고 가정한다. command line 대신에 IDE를 사용하고 싶으면 그래도 된다. 많은 IDE은 이제 어느정도 command line을 지원하고 있다; 사용하는 IDE의 문서를 확인해라. 최근에 rust팀은 IDE 지원을 하기 위해 노력하고 있고, 빠른 속도로 변화가 발생하고 있다!!

## creating a project directory

rust 코드를 저장할 디렉토리부터 만들어 보자. 어디서든 rust코드를 작성해도 되지만, 이책의 예제를 쉽게 따라하기 위해선, projects 디렉토리를 만들고, 그 안에 모든 프로젝트를 관리하기를 추천한다. 

터미널을 열고 아래의 명령어를 치자. 

```
$ mkdir ~/projects // projects 디렉토리 생성
$ cd ~/projects     // projects 디렉토리 내부로 이동
$ mkdir hello_world // hello_world 디렉토리를 만들기
$ cd hello_world    // hello_world 디렉토리 내부로 이동
```

## writing and running a rust program

다음으로, `main.rs`라는 이름의 새로운 source file을 만들자. rust 파일은 항상 `.rs` 확장자로 끝난다. 파일이름으로 두단어 이상을 사용하게 되면 `_`를 이용해서 단어를 분리해라. 예를 들어 `hello_world.rs`라고 써라. helloworld.rs 말고. 

main.rs라는 파일을 열고 아래의 내용을 써라. 

```
fn main() {
    println!("Hello, world!");
}
```

파일을 저장하고 터미널로 이동해라. Linux나 맥의 경우 아래의 명령어를 입력해서 컴파일하고 run해라.

```
$ rustc main.rs
$ ./main
Hello, world!
```

OS와 상관없이, `Hello, world!`가 출력된다. 만약에 잘안되면 이전챕터의 troubleshooting 부분을 확인해라. 

`Hello, world!` 가 출력되면 성공적으로 실행된것이다!!


## Anatomy of a rust program

"Hello, world!" 프로그램이 어떻게 동작하는지 리뷰해보자. 

```
fn main() {

}
```

위의 코드는 rust의 함수를 정의한다. `main`함수는 특별하다: 모든 실행가능한 rust 프로그램에서 `main`부터 실행된다. 첫번째 줄에서 `main` 함수를 정의하고, 파라미터가 없고, 아무것도 반환하지 않은다. 만약에 파라미터가 잇으면, 괄호 `()` 안에 써준다.


또한, 함수 body는 `{}`로 묶여 있다. rust의 모든 함수 body는  `{}` 로 둘러싸여있다. 함수이름과 같은줄에서 괄호를 시작하고 사이에 스페이스를 하나 넣어주는게 좋은 스타일이다. 

이 책이 쓰일당시엔 자동 formatter 툴 `rustfmt` 가 아직 개발중이다. 만약 rust 프로젝트에서 표준 스타일을 쓰고 싶으면, `rustfmt`가 포매팅을 해준다. rust는 `rustc`처럼 standard rust distribution에 `rustfmt`를 포함시키려고한다. 이책을 언제 읽는지에 따라서, 이미 설치가 되어있을 수도 잇다. 

`main` 함수 안에 아래 코드가 있다. 

```
println!("Hello, world!");
```

이 코드가 글자가 스크린에 찍어준다. 4가지 중요한 것이 있다. 

1. rust style은 `스페이스 네개로 인덴트`한다. tab이 아니라
2. `println!`은 rust 매크로이다. 만약에 이게 함수라면 ! 없이 `println`일것이다. 챕터 19에서 rust의 macro를 더 다룰 것이다. 여기선 우선 `!`를 쓰면 일반적인 함수가 아니라 macro를 부르는 것이라고 알면 된다. 
3. `println!`는 문자열을 인자로 받고 화면에 출력해준다. 
4. `;` 세미콜론으로 끝낸다. rust 코드의 대부분은 세미콜론으로 끝난다. 


## compiling and running are separate steps

방금 새 프로그램을 만들고 실행했다. 각 단계에 대해서 알아보자. 

rust 컴파일을 실해하기 전에 rust 컴파일러로 꼭 컴파일을 해야한다. 이건 `rustc`를 통해서 소스 파일의 이름을 넘겨주면 컴파일 할 수 있다. 

`$ rustc main.rs`

만약 c나 c++을 해봤으면 rustc가 `gcc` 나 `clang`과 비슷한걸 알 수 있다. 성공적으로 컴파일하면 rust는 바이너리 파일을 출력해준다(Binary executable).

Linux/macOS/PowerShell에서 `ls` 명령어를 통해서 실행 파일을 볼수 있다. 

linux/macOS에서는 아래처럼 두개 파일을 볼 수 있다. 

```
$ ls
main  main.rs
```

```
$ ./main # or .\main.exe on Windows
```
이 명령어를 통해서 "Hello, world!" 프로그램을 실행할 수 있다. 

만약 ruby, python, javascript와 같은 다이나믹 언어와 익숙하다면 컴파일하고 실행하는 것에 익숙하지 않을 수 있다. Rust는 _ahead-of-time-compiled_이다. 이런 언어들은 프로그램을 컴파일하고, 실행파일을 다른 사람에게 주면, 그사람이 rust 설치조차 안하고도 이 프로그램을 실행할 수 있다는 뜻이다. 만약 ruby, python, js의 경우 Ruby, Python, Javaascript 엔진이 설치되어야한다. 하지만 이런 언어에서는 명령어 한번에 컴파일하고 프로그램을 실행할 수 있다. 모든것이 언어를 디자인할때 trade-off이다. 

작은 프로그램은 `rustc`로만 컴파일해도 충분하지만, 프로젝트가 커지면 많은 옵션들을 다루거나, 코드를 공유하는것을 쉽게 하고 싶을 것이다. 다음장에서 `Cargo tool`을 통해서 실생활의 rust 프로그램을 작성해볼 것이다. 




