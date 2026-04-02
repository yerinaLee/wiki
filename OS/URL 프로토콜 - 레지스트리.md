## 1. URL 프로토콜
#### 1-1. 종류
**1. 일반 프로토콜**
일반 프로토콜은 OS/브라우저에 기본 탑재되어있음. 따라서 별도 등록 필요 없음
- http://
- https://
- ftp://
- mailto:

**2. 사용자 정의 프로토콜**
개발자가 직접 만든 프로토콜. 반드시 **레지스트리 등록**이 필요함
- kakaotalk://
- discord://
- zoommtg://
- gameqa:

#### 1-2. 형식
```
[프로토콜]:[데이터]
[프로토콜]://[데이터]
```
- 위 형태로 만든 URL로 브라우저에서 오픈한다.

- 호출 예시 js
```
window.location = uri;
```

#### 1-3. URL 프로토콜 호출 스텝
1. 브라우저가 `"gameqa"` 프로토콜 확인
- 기본 프로토콜 : 브라우저단에서 네트워크 호출
- 커스텀 프로토콜 : OS 레지스트리에서 프로토콜 서치

2. 레지스트리에 연결된 exe 실행
3. 뒤에 문자열 전체를 프로그램에 전달



## 2. 레지스트리

#### 2-1. 레지스트리 종류

```
HKEY_CLASSES_ROOT\[protocol]                    ← (통합 뷰)

HKEY_LOCAL_MACHINE\SOFTWARE\Classes\[protocol]  ← (모든 사용자 공통)
HKEY_CURRENT_USER\Software\Classes\[protocol]   ← (현재 사용자 전용)
```

- 만약 HKLM, HKCU 둘 다에 같은 프로토콜 경로가 있으면 HKCU가 우선순위임


#### 2-2. 레지스트리(HKLM, HKCU) 공통 구조
```
[protocol or extension]
 ├── (Default)         ← (설명)
 ├── URL Protocol      ← (프로토콜일 때만)
 └── shell
      └── open
           └── command ← (실제 실행)
```

- `[protocol]\URL protocol`
이 URL protocol 이 있어야 OS가 url 프로토콜임을 인식함. 값은 비어있어도됨
이게 없으면 파일 연결로 취급됨. 윈도우는 아래와 같이 구분함
|타입|예|
|---|---|
|파일|`.txt`, `.pdf`|
|프로토콜|`http://`, `myapp://`|

- `[protocol]\shell\open\command\(Default)`
이 프로토콜 호출을 통해 실제로 실행할 프로그램 경로
ex) 
```
해당 경로의 값

"C:\Program Files\MyApp\app.exe" "%1"
```
- `C:\Program Files\MyApp` 위치에 있는 `app.exe` 프로그램 실행
- `%1` : 전달된 URL 전체
OS는 전체 URL만 넘기기에 데이터 처리(프로토콜/데이터 분리)는 런처 내부에서 진행한다.

- 최종 프로그램 실행 커맨드
```
app.exe [protocol]:[data]
```
