# The Rust Programming Language

by Steve Klabnik and Carol Nichols, with contributions from the Rust Community

이 버전은 Rust 2018 Edition 구문 사용을 위해 Cargo.toml 에 `edition="2018"` 라고 되어있는 Rust 1.41.0 또는 그 이후버전을 사용하는 것을 전제로한다. 설치나 Rust업데이트를 위해서 Chapter1의 설치 파트를 살펴보거나 Appendix E를 참고하라. 

`The 2018 Edition of the Rust` 는 Rust를 더 쉽게 사용할 수 있는 변화가 있었다. 이 문서는 이러한 개선 사항들을 많이 반영했다. 

* Chapter7 은 “Managing Growing Projects with Packages, Crates, and Modules,” 은 거의 다 새로쓰였다. 2018 Rust에서는 모듈 시스템이나 paths 동작이 더 일관적이다. 

* Chapter10은 "Traits as Parameters"와 "Returning Types that Implement Traits" 라고, `impl Trait` 문법을 설명하는 섹션이 추가되었다. 

* Chapter 11은 “Using `Result<T, E>` in Tests” 는 `?`를 사용하는 테스트를 작성하는 섹션이 추가됬다. 

* Chapter 19에서는 “Advanced Lifetimes”는 컴파일러가 향상되면서 필요없어져서 빠졌다...

* 이전의 Appendix D, “Macros,”는 절차적인 매크로 내용이 포함되고, Chapter 19의 매크로 섹션으로 옮겨졌다. 

* Appendix A 의 "Keywords" 는 새로운 raw identifiers 기능(2015 edition 과 2018 edition이 상호작용 하기 위한 기능) 을 사용할 수 있는 방법에 대한 설명이 추가되었다. 

* Appendix D는  “Useful Development Tools” 라고 제목이 바뀌고, 새로 릴리즈된 Rust 코딩을 돕는 도구에 대한 설명을 한다. 

* 여러개의 작은 에러랑 정확하지 않은 언어 선택을 고쳤다. 읽어줘서 고마워~~

### 알아야할것!! 

_The Rust Programming Language_ Rust 컴파일러 버전을 업데이트 했더라고, 이전버전의 코드는 edition="2018"(Cargo.toml) 없이 계속 컴파일될것이다. 이건 Rust의 backward compatibility라는 거다!!

https://doc.rust-lang.org/stable/book/ 에서 html버전으로도 볼수있고, rustup으로 설지된 오프라인 버전으로도 볼수 있다.(rustup docs --book)

https://nostarch.com/Rust2018 에서 책이 있다!