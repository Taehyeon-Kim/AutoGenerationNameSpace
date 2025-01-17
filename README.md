# AutoGenerationSwiftNameSpace
🐮 내 맘대로 만드는 네임스페이스 자동 생성기(feat. python)

> 👉 왜 이렇게 까지 해야해? 라는 의문이 들 수 있을 것 같습니다.  
> 저도 처음에는 그렇게 생각했거든요.

> 협업을 하다보니 서로 파일 · 에셋 · 변수명에 대한 부분을 논의하는 것이 생각보다 까다로운 작업이라는 것을 느꼈고,   
> 개발 파트 내에서도 더 나아가 디자이너, 기획자와의 협업에 있어서도 어느 정도 네이밍이 통일되어 사용되는 것이 중요하다는 생각이 들었습니다.

> 👉 그러면 또 문서를 작성하면 되는 거 아니야?, 피그마나 노션 가이드라인 있잖아! 라고 생각이 들 수 있는데  
> 1. 해당 작업은 매 빌드 시 스프레드시트를 가져와 스크립트를 돌리기 때문에 스프레드시트 상에서 업데이트가 이루어지면  
> Xcode 프로젝트내에서도 값이 바로 반영이 되는 장점이 있습니다.  
> 개발자가 직접 프로젝트 내에서 일일이 변경하는 번거로움을 덜어줄 수 있죠.

> 2. 또 하나 좋다고 생각하는 부분이 파트 내에서 네이밍에 대한 부분을 좀 더 효율적으로 정할 수 있다는 것 같습니다.  
> 스프레드시트를 보면서 같이 얘기해서 뷰컨, 스토리보드, 에셋 등의 네이밍을 하고 정리를 하면  
> 서로 정리가 되고 또, 프로젝트에도 바로 반영이 된다는 장점이 있는 것 같습니다.

> 위에서 언급한 장점 때문에 다음 프로젝트에 한 번 사용해보려고 생각 중이구요..🙄  
> 🚨 근데 그냥 SwiftGen, R.swift 쓰는게 더 나을 것 같아요 ㅎㅎ (저는 1,2번 장점 때문에 쓰려고 합니다!!)

<br />

## Usage

#### 1. 구글 스프레드시트
> 네임스페이스, 상수라고 불리우는 값들을 작성합니다.

> ⛔️ 현재 이미지에서 보이는 것처럼 Text, Color, Image, Storyboard, Xib를 기준으로 스크립트가 작성되어 있습니다.  
> ⛔️ 그래서 이미지처럼 내용을 스프레드시트를 작성하시거나, 파이썬 스크립트를 일부 수정해서 사용하시기 바랍니다.

![스크린샷 2021-12-25 오전 3 28 56](https://user-images.githubusercontent.com/61109660/147368969-e98f7914-3f29-419d-9e0d-bb7f36a92364.png)

#### 2-1. 파이썬 파일 추가
> 저 같은 경우는 script라는 폴더를 만들고 하위 항목으로 파이썬 파일을 넣어주었습니다.

![스크린샷 2021-12-25 오전 3 44 44](https://user-images.githubusercontent.com/61109660/147369203-27521d2e-f450-4313-86b6-18bdbfc6ca67.png)

#### 2-2. 스프레드시트 아이디 추가

본인이 구글 드라이브에 생성한 스프레드시트의 아이디를 추가하는 작업이 필요합니다.

generate.py 파일의 gdoc_id로 선언된 부분에 url의 ~/d/ 뒷부분의 값을 넣어주시면 됩니다.

<img width="758" alt="스크린샷 2021-12-26 오전 1 25 14" src="https://user-images.githubusercontent.com/61109660/147389313-aab35c53-0678-445b-b3a8-10e8a001142c.png">

```python
gdoc_id = "1WMnHk1brX7CR34hCN88cDnTDc4UgTAKh-qegwnPIqCU/edit#gid=0"
```

#### 2-3. Xcode 파이썬 실행 스크립트 추가 
> [Build Phase] - [Run Script] 부분에 스크립트를 추가합니다.

`ex`
```
python ${TARGET_NAME}/script/generate.py ${TARGET_NAME}
```

#### 3. 생성된 파일과 폴더를 Xcode 프로젝트 내에 추가합니다.

![스크린샷 2021-12-25 오전 3 40 24](https://user-images.githubusercontent.com/61109660/147369080-2ff105ed-1d1b-49f5-8b77-754621aab36b.png)

> 생성된 폴더를 프로젝트 내로 드래그 하면 됩니다.
<img width="800" alt="스크린샷 2021-12-25 오전 3 41 41" src="https://user-images.githubusercontent.com/61109660/147369106-224ea05d-b043-4b25-8a45-ded80bb11daf.png">

#### 4. 그럼 예쁘게 생성된 네임스페이스(상수) 파일을 볼 수 있습니다.
<img width="463" alt="스크린샷 2021-12-25 오전 3 43 06" src="https://user-images.githubusercontent.com/61109660/147369162-ecaaa4d8-29bc-46ff-8bc0-6ce39e6368f1.png">
<img width="451" alt="스크린샷 2021-12-25 오전 3 43 21" src="https://user-images.githubusercontent.com/61109660/147369156-046316f5-62b1-40e3-bf34-17afb06ce9a2.png">
<img width="614" alt="스크린샷 2021-12-25 오전 3 43 26" src="https://user-images.githubusercontent.com/61109660/147369154-e7bf640b-09b6-409b-8ec5-4f03b747f950.png"><img width="389" alt="스크린샷 2021-12-25 오전 3 43 16" src="https://user-images.githubusercontent.com/61109660/147369158-7e7a10b6-2153-4975-ae41-eb6fcfa3017d.png">
<img width="527" alt="스크린샷 2021-12-25 오전 3 43 12" src="https://user-images.githubusercontent.com/61109660/147369160-fbc9207f-0f83-4b2a-a039-ba973f181a36.png">

#### 5. 구글 스프레드시트에 값을 업데이트하면 자동으로 프로젝트 내의 파일에도 반영이 됩니다.

<br />

## Trouble

> python 파일에 외부에서 설치하는 모듈이 있으면 Xcode 상에서 정상 동작하지 않는 문제가 있습니다.  
> openpyxl 라이브러리를 써서 xlsx 파일로 관리하려 했으나 그게 되지 않아, 내장 모듈인 csv 모듈을 이용해서 작업했습니다.

<br />

## Reference

https://macgongmon.club/m/26

> 다음 블로그에서 영감을 받아 작업했습니다.  
> 파이썬 스크립트의 대부분의 코드를 가져왔으며, 일부분만 수정했습니다.
