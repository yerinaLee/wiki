## 프로토콜
#### 종류
1. 일반 프로토콜
2. 사용자 정의 프로토콜

#### 형식
\[프로토콜]:\[데이터]
\[프로토콜]://\[데이터]

### 1) 일반 프로토콜

사용자 정의 프로토콜 호출

?? 그럼 전체 정의 프로토콜은 http, https 이런건가?
🌐 일반(기본) 프로토콜
OS/브라우저에 기본 탑재:
http://
https://
ftp://
mailto:

👉 별도 등록 필요 없음

🛠 사용자 정의 프로토콜
개발자가 직접 만든 것:
kakaotalk://
discord://
zoommtg://
happytuk-fs1qa:
👉 반드시 레지스트리 등록 필요



1. url 형식 
[프로토콜] : [데이터] 형태로 브라우저에서 오픈한다.

```
window.location = uri;
```

HKEY_CLASSES_ROOT\[ protocol ]

HKEY_CLASSES_ROOT\[ protocol ]\URL protocol
- 여기서 URL protocol 이 있어야 OS가 url 프로토콜임을 인식함. 값은 비어있어도됨
?? 이게 없으면 url로는 호출 못하는거야?


HKEY_CLASSES_ROOT\[ protocol ]\sell\open\command\(Default)
- 실제로 실행할 프로그램 경로
ex) 
```
"C:\Program Files\MyApp\app.exe" "%1"
```
- %1 : 전달된 URL 전체
프로토콜까지도 같이 넘기는건, OS는 전체 URL만 넘기기에 데이터 처리는 런처 내부에서 진행한다.


* HKEY_CLASSES_ROOT(HKCR) : 통합 뷰

HKEY_LOCAL_MACHINE\SOFTWARE\Classes   (모든 사용자 공통)
HKEY_CURRENT_USER\Software\Classes    (현재 사용자 전용)

이 둘을 합쳐서 보여준다. 아래 경로에서 찾을수있음
HKEY_CLASSES_ROOT(HKCR)\ [ protocol ]

- 만약 HKLM, HKCU 둘 다에 같은 경로가 있으면 HKCU가 우선순위


* HKLM, HKCU 공통구조

[protocol or extension]
 ├── (Default)         ← (설명)
 ├── URL Protocol   ← (프로토콜일 때만)
 └── shell
      └── open
           └── command ← (실제 실행)



1. 지금 프로토콜이 호출된 레지스트리 경로는
컴퓨터\HKEY_LOCAL_MACHINE\SOFTWARE\Classes\happytuk-fs1qa\shell\open\command

인데, HKEY_CLASSES_ROOT 랑 HKEY_LOCAL_MACHINE는 어떤 차이야?
그리고 각 경로가 디폴트로 갖고 있는 공통적인 구조가 있다면 특징들을 알려줘


2. 결국 실행은 이렇게 됨:
app.exe "myapp://something" 이라고 했는데, 이부분이 좀 이해가 안가.
이미 myapp 은 프로토콜로 저 app.exe 파일을 찾는데에 쓰였잖아? 그럼 %1에는 그 뒤 something 부분의 data만 넘어가는거아냐?


3. HKEY_CLASSES_ROOT\[ protocol ]\URL protocol
- 여기서 URL protocol 이 있어야 OS가 url 프로토콜임을 인식함. 값은 비어있어도됨
?? 이게 없으면 url로는 호출 못하는거야?


4. 사용자 정의 프로토콜 호출
?? 그럼 일반 정의 프로토콜은 http, https 이런건가?