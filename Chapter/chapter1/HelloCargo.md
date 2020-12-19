# Hello, Cargo!

Cargo는 rust의 빌드 시스템이나 패키지 매니저이다. 많은 Rustaceans는 rust 프로젝트를 cargo를 이용해서 관리한다. 왜냐하면 Cargo가 코드를 빌드하거나, 라이브러리를 다운로드하거나, 다운로드 받은 라이브러리들을 빌드하는 등의 많은 태스크들을 처리해주기 때문이다. (코드에서 필요한 라이브러리들을 디펜던시라고 한다)

우리가 이전 장에서 만든 프로그램처럼 엄청 간단한 것들을 아무런 디펜던시가 없다. 그래서 "Hello, world!" 프로젝트를 빌드하기 위해 Cargo를 사용하면 Cargo가 단지 우리의 코드를 빌드하는데만 쓰인다. 더 복잡한 Rust프로그램을 만들게 되면, 디펜던시도 더하게 될것인데, `Cargo`를 이용하면 이런 dependency를 관리하는 것이 훨씬 쉽다. 

많은 Rust프로젝트들이 Cargo를 사용하지 때문에 책의 나머지 부분에서는 Cargo를 사용한다고 가정할 것이다. Cargo는 Rust를 설치할때 같이 설치되고, Installation sectiondp에서 내용을 확인할 수 있다. 다른 방법으로 Rust를 설치했다면(rustup 이외의 방식) 아래의 명령어를 터미널에 입력해서 cargo가 있는지 확인해라. 

`$ cargo --version`

버전 넘버가 보이면 가지고 있는것이다. 만약 `command not found`같은 결과가 뜨면, 문서를 보고 어떻게 cargo를 따로 설치할 수 있는지 알아봐라. 


## Creating a project with Cargo

cargo를 이용해서 새로운 프로젝트를 만들고 이게 기존의 "Hello, world!"프로젝트와 어떻게 다른지 보자. 프로젝트 디렉토리로 돌아가자(당신이 작업하는 곳으로 가라). 

```
$ cargo new hello_cargo
$ cd hello_cargo
```
위를 터미널에 입력해서 프로젝트를 생성해라. 
첫번째 명령은 hello_cargo라는 디렉토리를 생성한다. 우리는 hello_cargo라는 이름의 프로젝트를 생성하고, cargo는 필요한 파일을 이안에 생성한다. 

hello_cargo 폴더 안에 들어가서 파일을 살펴보자. Cargo가 두개의 파일과 한개의 디렉토리를 생성한 것을 확인할 수 있다: `Cargo.toml` 파일, `src` 폴더, 그리고 `src 폴더 내의 main.rs` 파일


또한 깃 리포지토리도 하나 생성되고 `.gitignore` 파일도 생성된다. 깃 파일은 existing git repository내에서 `cargo new`를 하는 경우 생성되지 않는다. 만약 이경우에 깃파일을 생성하고 싶다면 `cargo new --vcs=git` 를 통해서 시작할 수 있다. 

* Note: 깃은 버전 컨트롤 시스템이다. `--vcs`를 통해서 `cargo new`가 다른 버전 컨트롤 또는 아예 사용하지 않도록 변경할 수 있디. `cargo new --help`를 통해서 이용가능한 옵션을 확인 할 수 있다. 

`Cargo.toml` 을 열어보자. 

```
[package]
name = "hello_cargo"
version = "0.1.0"
authors = ["Your Name <you@example.com>"]
edition = "2018"

[dependencies]
```
위의 파일은 [TOML](https://toml.io/en/) (Tom’s Obvious, Minimal Language) 포맷으로 Cargo의 설정 포맷이다. 

첫번째 줄 `[package]`는 다음에 나오는 내용이 패키지 설정내용이라는 것을 표시한다. 점차 이파일에 더 많은 정보를 넣게되면, 다른 섹션도 포함하게 될것이다. 

`[package]` 의 네가지 정보는 Cargo가 프로그램을 컴파일하기 위해서 필요한 내용이다: name, version, 누가 썼는지랑 이메일, `edition` 정보. `edition`은 Appendix E에서 상세히 다룰 것이다. 

마지막 라인인 `[dependencies]`는 프로젝트의 디펜던시를 위한 섹션을 시작하는 헤더이다. Rust에서는 패키지를 `crates`라고 부른다. 우리는 이 프로젝트를 위해서 다른 crates가 하나도 필요없지만 Chapter2에서는 dependecies 섹션에 대해서 더 다룰 것이다. 


이제 `src/main.rs`를 열어보자. 

```
fn main() {
    println!("Hello, world!");
}
```

Cargo가 "Hello, world!" 프로그램을 만들어 줬다. cargo가 만들어준 프로그램과 이전 챕터에서 생성한 프로젝트의 차이점은 이번건 src 폴더내에 main.rs가 있다는 것과 cargo.toml파일이 있다는 것이다. 

Cargo는 우리의 소스코드가 src 폴더내에 있기를 예상한다. 프로젝트 최상단은 README 파일, 라이센스 정보, configuration files 그리고 소스코드와 관령되지 않은 정보를 저장하는 곳이다. Cargo를 사용하면 프로젝트를 구조화하기 수월하다. 모든것이 자기의 위치가 있고, 모든것이 자기가 있어야할 곳에 있다. 

만약 프로젝트를 Cargo없이 만들었다면 Cargo를 사용하는 프로젝트로 변경할 수 있다. 코드를 src폴더내로 옮기고, Cargo.toml파일을 생성해라. 


## Building and Running a Cargo Project

Cargo를 사용해서 프로젝트를 만들면 어떻게 다른지 살펴보자. hello_cargo 디렉토리에서 아래의 명령을 통해 프로젝트를 빌드 해보자.

```
$ cargo build
   Compiling hello_cargo v0.1.0 (file:///projects/hello_cargo)
    Finished dev [unoptimized + debuginfo] target(s) in 2.85 secs
```

위의 명령은 target/debug/hello_cargo 안에 실행파일을 생성한다(현재 위치에 생성하는 것이 아님).  아래의 명령을 통해 실행파일을 실행할 수 있다. 

```
$ ./target/debug/hello_cargo # or .\target\debug\hello_cargo.exe on Windows
Hello, world!
```

다 잘되면 `Hello, world!`라고 출력할 것이다. `cargo build`를 처음으로 실행하면 최상위 경로에 `Cargo.lock`파일을 생성할 것이다. 이 파일은 내가 사용한 정확한 버전 정보를 기록한다. 이 프로젝트는 아무런 디펜던시가 없어서 파일이 거의 비어있다. 이 파일을 수동으로 바꿀일은 없을것이고, cargo가 이걸 관리해줄 것이다. 

방금 `cargo build`로 프로젝트 생성했고, `.\target\debug\hello_cargo`를 실행해서 프로젝트를 실행할 수 있다. 하지만 또 `cargo run`을 사용해서 실행할 수도 있다. `cargo run`은 코드를 컴파일하고 run 할 수 있다. 

```
$ cargo run
    Finished dev [unoptimized + debuginfo] target(s) in 0.0 secs
     Running `target/debug/hello_cargo`
Hello, world!
```

지금 위의 cargo run을 수행하면 hello_cargo를 컴파일하고 있지 않다는 것을 볼수 있다. Cargo는 파일이 변하지 않았단 것을 파악하고, 그냥 바이너리 파일만 실행했다. 만약 소스코드를 변경했다면, cargo가 프로젝트를 다시 빌드하고 실행할 것이고 아래 메시지를 볼 수 있을 것이다. 

```
$ cargo run
   Compiling hello_cargo v0.1.0 (file:///projects/hello_cargo)
    Finished dev [unoptimized + debuginfo] target(s) in 0.33 secs
     Running `target/debug/hello_cargo`
Hello, world!
```

Cargo는 `cargo check`라는 명령어도 제공해준다. 이건 빠르게 내 코드가 컴파일 가능한지 확인하지만 실행파일(executable)은 생성하지 않는다. 

```
$ cargo check
   Checking hello_cargo v0.1.0 (file:///projects/hello_cargo)
    Finished dev [unoptimized + debuginfo] target(s) in 0.32 secs
```

왜 executable을 안 생성하는걸까? 주로 `cargo check`는 `cargo build`보다 빠르다. 왜냐하면 실행파일을 생성하는 단계를 건너뛰기 때문이다. 만약 코드를 작성하는 동안 계속 `cargo check`를 이용하면 작업속도를 빠르게 할 수 있다. 그래서 많은 Rustaceans 은 `cargo check`를 주기적으로 실행해서 코드가 컴파일 되는지 확인한다. 그리고  실행 파일을 생성할 준비가 됬을 때 `cargo build`를 이용한다. 

우리가 Cargo에 대해서 지금까지 배운걸 정리해보자. 

* `cargo build`를 통해서 프로젝트를 빌드 할 수 있다. 
* `cargo run`을 통해서 프로젝트를 빌드하고 실행할 수 있다. 
* `cargo check`를 통해 바이너리 파일을 생성하지 않으면서 에러가 있는지 확인하기 위해 빌드 할 수 있다. 
* 코드 위치에 바이너리 코드를 저장하는 것이 아니라, `target/debug`안에 바이너리 파일을 생성한다. 

추가적인 Cargo의 장점은 어떤 os이던가간에 cargo 명령이 똑같단 것이다. 그래서 이제 linux/macOS, 윈도우에 따라서 다른 설명사항을 제공하지 않을 것이다. 


## Building for Relase

만약 코드가 relase 준비가 되면 `cargo build --release`를 통해서 최적화된 컴파일을 할 수 있다. 이명령은 `target/debug`가 아니라  `target/release`안에 실행파일을 생성한다. 최적화는 Rust코드가 더 빠르게 하지만 컴파일 시간은 좀더 오래걸린다. 이것이 컴파일하는데 두가지 버전이 있는 이유이다: 하나는 개발모드 - 빨리 자주 빌드하고 싶을때, 다른경우는 최종 빌드하는 경우 - 반복적으로 빌드될 필요가 없고, 최대한 빠르게 동작하는 실행파일을 만드는 것. 코드의 실행속도를 벤치마크할때, `cargo build --release`를 하고 `target/release` 안에 있는 실행파일을 기준을로 확인하도록 하자. 



## Cargo as Convention

작은 프로젝트에서는 Cargo가 `rustc`보다 큰 장점을 보여주진 않는다. 하지만 프로젝트가 복잡해질수록 점점더 많은 도움을 줄것이다. 많은 crates를 포함하는 복잡한 프로젝트에서는 Cargo가 빌드를 조정하는 것이 훨씬 편하다. 

`hello_cargo`프로젝트는 간단하지만, Rust 커리어에서 필요한 실제 툴을 많이 사용하고 있다. 사실, 어떠한 기존 프로젝트를 git을 통해 clone하고, 해당 프로젝트 내부로 이동한다음,  빌드할 수 있다. 

```
$ git clone someurl.com/someproject
$ cd someproject
$ cargo build
```

Cargo에 대해서 [추가적인 문서](https://doc.rust-lang.org/cargo/)를 확인해라. 

## Summary
Rust 여정을 떠날 준비가 됬다. 이 챕터에서 아래의 내용을 배웠다. 

* `rustup`을 통한 Rust 의 latest stable version 설치
* 새로운 Rust 버전으로 업데이트
* 로컬에 설치된 문서를 여는 방법
* 프로젝트를 작성하고, `rustc`를 통해서 프로젝트를 실행하는 방법
* Cargo를 사용해서 프로젝트를 생성하고 run 하는 방법

Chapter2에서는 숫자 맞추기 게임을 만들것이다. Rust 프로그래밍 컨셉에 대해서 먼저 알고싶으면 Chapter3부터 확인한다음 Chapter2를 확인해라. 

[출처](https://doc.rust-lang.org/book/ch01-03-hello-cargo.html)