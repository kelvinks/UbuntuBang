# MDwiki

## [이 사이트](http://dymaxionkim.github.io)를 만든 방법 요약
### 00. 일러두기
본 사이트는 MDwiki를 Github에 올려서 호스팅하고 있습니다.  그리고 MDwiki의 부족한 기능을 보완하기 위하여, DISQUS(댓글기능)와 Prose.io(편집기능)을 가져다가 붙였습니다.  개인 사이트 구성을 위해 Github를 선택하고, 적절한 위키시스템으로 MDwiki를 골라내기까지 이전에 상당히 다양한 서비스와 솔루션을 테스트 해 봤었는데 구체적인 내용은 생략합니다.  아무튼 최종적으로 Github + MDwiki 조합이 가장 단순무식해서 내 마음에 듭니다.  본 설명 내용은 [이곳](http://dynalon.github.io/mdwiki/#!tutorials/github.md)을 참고하였습니다.
### 01. [GitHub](https://github.com)에 가입
일단 무조건 가입합니다.  Github는 분산형 소스코드 버전관리 유틸리티인 Git을 호스팅해주는 거대한 규모의 서비스입니다.  Github에 대항하는 다른 서비스들도 여럿 있지만 규모면에서 상대가 안됩니다.  Git이나 Github가 대체 뭔지 정확히 잘 모른다면, 그냥 시간이 지나면서 자연히 알게 될 테니 고민하지 마시고, 이 서비스가 제공해주는 많은 기능 중에서 내가 필요한 것만 몇 가지 골라서 그것만 쓰도록 합시다.
### 02. GitHub의 환경설정
가입하고 나면 대체 여기서 뭘 해야 할지 막막합니다.  그럼 생각을 하지 마시고,  아무것도 하지 맙시다.  셋팅할 것이 없습니다. (ㅋㅋ)
### 03. [MDwiki](http://www.mdwiki.info)를 Fork
MDwiki라는 것은, 웹사이트 서비스의 골격을 미리 만들어놓은 프레임웤의 하나라고 생각됩니다.  보통 이런 웹사이트 제작용 프레임웤은 WordPress나 ExpressEngine 처럼 엄청나게 복잡한 것들이 많습니다.  개인 사이트 하나 꼴랑 만드는데 굳이 이런 복잡한 걸 써야되나?  당연히 아주 간단한 걸 찾게 됩니다.  간단한 거 중에서 특히 엄청나게 제일 간단한 것 중의 하나가 바로 MDwiki 였습니다.  MDwiki는 html 파일 달랑 하나가 다입니다.  'index.html'이라는 이름으로 호스팅 서버에 올려두면, 외부에서 웹브라우저로 이 index.html을 읽어서 보게 되는데, 이 파일 안에 Javascript 스크립트가 들어있기 때문에, 그게 외부에서 보는 사람의 웹브라우저에서 다운로드되어 실행되면서 필요한 화면을 구성해 주고 내용을 보여주게 됩니다.  따라서 MDwiki는 호스팅 서버(여기서는 Github) 쪽에서는 전혀 아무런 프로그램도 돌아가는 것이 없고, 전부 다 외부에서 index.html을 읽어다가 보는 사람들의 웹브라우저 즉 클라이언트 쪽에서 전부 프로그램이 돌아갑니다.  서버에서 돌아가는 프로그램이 없으므로, 서버 쪽에 아무런 프로그램 실행환경을 구성해 줄 필요가 없습니다.  단지 웹호스팅만 해 주면 되죠.
또, MDwiki는 이런 저런 잡스러운 위키 문법 같은 것 대신 요즘 특히 핫한 마크다운 문법을 지원합니다.  따라서 글쓰기가 편하므로 컨텐츠를 계속 불려 나가기 좋습니다.
아무튼 뭐 그건 그렇고, MDwiki를 어디서 다운로드 받아다가 내 컴퓨터에서 무슨 셋팅을 해 주고 어쩌구 할 필요 없이, Github를 이용하는 다른 사람의 방들 중에서 MDwiki를 굴리고 있는 곳을 찾아서, 마음에 드는 놈을 Fork 하면 내 방으로 가져올 수 있습니다.
일단 Github 사이트의 검색창에서 `mdwiki` 키워드로 검색해 보면 매우 많은 숫자의 방들이 목록으로 주루룩 나옵니다.  이것들 중에서 맘에 드는 녀석으로 골라 봅니다.  내 경우에는 제일 간단한 이곳( https://github.com/Dynalon/mdwiki-examples/tree/gh-pages/cafe )을 주로 참고하였습니다.  제일 노말한 것 같습니다.  여기서 `Fork` 버튼을 찾아서 누르면 Fork가 됩니다.  즉 자동으로 나의 방이 하나 만들어지면서 거기에 통째로 순식간에 복사가 됩니다.  그리고 이미 이 방에 내가 들어와 있습니다.
### 04. MDwiki의 환경설정
위에 `Settings` 버튼을 찾아서 눌러 봅니다.  이제 이 방을 셋팅하는 페이지가 나옵니다.  제일 먼저 할 일은 `Repository name`을 변경합니다.  방이름은 아무거나 하지 말고, 반드시 `나의계정.guthub.io`로 해 줍시다.  이렇게 하면 나중에 이 방에서 호스팅해주는 홈페이지 주소가 `http://나의계정.guthub.io`이 됩니다.  만일 임의의 이름으로 방을 만들게 되면 홈페이지 주소는 자동으로 `http://나의계정.guthub.io/방이름`이 됩니다. 'Features' 카테고리에 있는 것들 중에서 'Issues'만 체크해서 사용하도록 합시다(Issues에 그림을 직접 업로드 해서 쓸 수 있습니다.).  그 밑의 'Launch Automatic page generator'라는 버튼은 누르지 맙시다.  Github에서 홈페이지를 자동으로 생성해주는 도구인데 이걸 사용하지 않을 것이니까요.  이제 셋팅 다 끝났으면 빠져나옵니다.  저장이나 OK버튼이 없고 자기가 알아서 이미 저장했으므로 셋팅이 안 먹을 걱정은 안해도 됩니다.
### 05. 사이트 잘 되는지 확인
웹브라우저 새 탭에서 `http://나의계정.guthub.io` 주소로 들어가 봅니다.  잘 뜨는지 확인해 봅시다.  내용이야 Fork해 온 원본 그대로니깐 감안하시고요.
### 06. [Prose.io](http://prose.io)에 가입
이제 내용편집을 해야 할텐데, Github에서 편집을 원하는 파일로 들어가서 직접 편집해도 됩니다만 여러모로 불편하고, 특히 한글 입력이 잘 안됩니다.  아주 거지같습니다.  그래서 외부의 다른 온라인 편집기 서비스를 갖다 쓰려고 합니다.  여러가지 좋은 것들이 있는데 그 중에 Github와 찰떡궁합이 제일 좋은 Prose.io를 이용하기로 합시다.  http://prose.io 사이트로 들어가면 되고, 회원가입은 별도로 아이디를 만들 필요 없이 이미 가입한 Github 계정으로 소셜계정 로그인이 됩니다.  로그인하면 나의 Github의 방이 보이면서 안에 파일들도 다 보입니다.  원하는 파일을 찝어서 편집해 주고 저장하면 자동으로 Github에 반영이 되어서 바로 보이게 됩니다.  필요없는 파일을 지우거나, 새로운 파일을 만들어서 내용을 써 넣거나, 기존 파일을 열어서 편집하는 것이 모두 즉각 됩니다.
### 07. 무슨 파일을 편집해야 할까?
`index.html` 파일은 MDwiki의 핵심 엔진이므로 조심스럽게 다룹시다.  파일을 Prose.io에서 열어서 보면 코드가 어지럽게 들어 있습니다.  다른 곳은 건드릴 필요 없고, `<title>MDwiki</title>`라는 곳의 문구만 수정해 줍시다.  내 홈페이지의 이름이죠.  웹브라우저의 탭에서 보이는 이름입니다.  수정 후에 'Ctrl-s'를 누르면 저장됩니다.  아니면 우측에 저장 단추 누르고 Commit 해 주시면 됩니다.
그 다음에 `config.json` 파일을 열어봅시다.  MDwiki 설정파일이라고 보시면 되겠죠.  'additionalFooterText', 'title' 항목의 내용만 건드려 주시면 됩니다. ([참고1](http://dynalon.github.io/mdwiki/#!customizing.md), [참고2](http://dynalon.github.io/mdwiki/#!layout.md))
그 다음에는 `index.md` 파일을 열어서 편집합시다.  첫번째 페이지 이므로 마크다운 문법([문법설명](http://dynalon.github.io/mdwiki/#!quickstart.md))으로 대충 줄줄 써 줘 봅시다.
그 다음에는 `navigation.md` 파일을 열어서 편집합시다.  편집 요령은 [이곳](http://dynalon.github.io/mdwiki/#!quickstart.md) 중에서 'Adding a navigation'를 참고합시다.  참고로, 여기서 메뉴를 구성할 때 `[EDIT](http://prose.io)` 메뉴를 하나 만들어 줍시다.  홈페이지 편집을 즉각즉각 하기가 편해집니다.
이런 식으로 해서 사이트를 구성해 갑니다.  편집 작업후 저장하면 홈페이지에 반영되는지 확인해 가면서 작업하면 됩니다.
### 06. DISQUS에 가입
댓글 시스템을 달고 싶으면, 역시 MDwiki 자체적으로 제공하지 않으므로 외부 서비스를 끌어다 붙이면 됩니다.  MDwiki는 자체 기능이 미약한 대신, 외부 서비스를 끌어다 붙이기 좋도록 '기믹(Gimmick)'이라는 기능이 있습니다.  [이곳](http://dynalon.github.io/mdwiki/#!gimmicks.md) 중에서 'DISQUS' 항목을 참고 합니다.
DISQUS 역시 새로운 아이디를 만들 필요 없이, 구글/페이스북/트위터 중의 하나의 계정으로 소셜계정 로그인이 됩니다.  DISQUS 서비스는 무조건 3개 이상의 디스커스를 골라서 팔로잉을 해 줘야 자신의 디스커스를 생성할 권한을 줍니다.  커뮤니티 활성화를 통해 회사 가치를 올리려는 마케팅 전략인가보죠.  뭐 돈 드는 것도 아니므로 아무거나 3개 정도 예의상 팔로잉해 줍시다.
### 07. DISQUS 환경설정
이제 내 홈페이지에 붙여넣을 댓글 디스커스를 만들어야 할텐데, 어디로 가야할지 막막합니다.  `View Addmin` 또는 `ADD DISQUS TO YOUR SITE` 같은 버튼이 보인다면 눌러서 들어갑니다.  페이지가 바뀌면 여러 웹서비스 아이콘이 보이는 페이지로 들어가 지는데, 우리는 Tumblr 같은 웹사이트는 아니므로 `Universal Code`를 선택해 줍니다.  이제 또 페이지가 바뀌는데, 셋팅 화면이죠.  좌측 메뉴중에서 'Basic'을 눌러 봅니다.  뭐 이것저것 건드릴 필요 없이 죽 보면 'Site Identity' 카테고리에, 내가 댓글 디스커스를 붙여줄 나의 홈페이지 주소를 적어주고 이름 적어주면 되겠죠.  여기서 `Shortname` 항목에 보이는 나의 Shortname을 반드시 기억해 둡니다.  이제 다 됐으면 맨 아래 `Save Changes` 버튼 눌러주고 빠져나옵시다.  이제 셋팅 끝.
### 08. DISQUS 기믹(Gimmick) 붙이기
navigation.md 파일 안에 [이곳](http://dynalon.github.io/mdwiki/#!gimmicks.md) 중에서 'DISQUS' 항목 내용을 참고해서 그 형식 그대로 써주면 됩니다.  물론 아까 기억해 둔 Shortname을 사용하고요.  그리고 저장하고 나와서 확인해 보면 댓글 디스커스가 붙어 있음을 볼 수 있습니다.
```
[gimmick:Disqus](your_disqus_shortname)
```
이런 식으로요.
금방 만든 댓글 디스커스는 1개 뿐이고, 이걸 navigation.md에 적용했기 떄문에, 나의 웹사이트 어느 페이지어서든지 전부 동일한 댓글 디스커스가 붙습니다.
만일 페이지마다 댓글 시스템을 다르게 먹이고 싶다면, DISQUS에서 반복적으로 필요한 개수 만큼의 댓글 디스커스를 만들어주고(물론 Shortname은 전부 잘 정해서 다르게 하고요), 기믹(Gimmick)을 Navigations.md가 아닌 각각의 .md 파일마다 따로 써 넣어주면 됩니다.
### 09. 결론
이상의 방법으로, 자신의 PC에 어떤 파일이나 프로그램도 다운로드 받지 않고 전부 온라인으로 홈페이지를 뚝딱 만들었습니다.  기능과 디자인이 단순무식한 대신 내용 자체에 집중하기가 용이하다고 생각됩니다.  MDwiki 자체에 편집기능이 없는 대신 Prose.io 서비스를 끝어다 붙여서 보완했습니다.


----
## Julia 웹서버 설치

* Julia로 할 수 있는 몇가지 작은 웹서버 및 프레임웤들이 있는 것 같은데, 그중에 제일 간단한 것으로 해 봅시다.  여기서는 HttpServer.jl ( https://github.com/JuliaWeb/HttpServer.jl )을 선택해 보았습니다.

* 설치하기 전에 우선 의존성 있는 C라이브러리의 빌드가 가능하게 하는 cmake 패키지를 먼저 설치합니다.  이것을 설치하지 않으면 HttpServer.jl의 설치 과정중에 MbedTLS라는 라이브러리를 빌드하다가 실패한다고 나옵니다. (참고 : https://github.com/JuliaWeb/MbedTLS.jl/issues/7 )
```
sudo apt-get install cmake
```

* 그리고 Julia를 실행하고, julia REPL 환경상에서 HttpServer 패키지를 설치합니다.
```
Pkg.add("HttpServer")
```

* 이제 작동하는지 여부를 확인하기 위해 테스트 해 봅니다. ( 참고 : https://github.com/JuliaWeb/HttpServer.jl/blob/master/docs/HttpServer.md )
```
cd /home/dong/.julia/v0.4/HttpServer
julia examples/hello.jl
```

* 웹브라우저 주소창에 `localhost:8000/hello/name`를 쳐 봅니다.  페이지가 뜨는지 확인.



----
## 초간단한 Python 웹서버 스크립트로 간단히 MDwiki를 직접 호스팅 해 보기

* Python으로 작성된 초간단한 웹서버 스크립트가 있길래 한 번 사용해 보았습니다. ( http://linuxspot.tistory.com/224 )

* 위 사이트에 소개된 소스코드를 편집기로 내용을 복사해 넣고, 'miniWebServer.py' 이름으로 해서 로컬 컴퓨터의 MDwiki 메인 디렉토리 (index.html 파일이 있는 곳)에 저장해 넣습니다.

* 그 다음에, 'miniWebServer.py' 파일의 권한을 '실행가능'으로 바꿔줍니다.  `chmod +x miniWebServer.py` 정도 명령이면 될 것 같습니다.

* 그리고 `./miniWebServer.py 8000`으로 명령을 주면 초미니 웹서버가 실행됩니다.

* 웹브라우저 주소창에서 'localhost:8000'을 쳐 보면 MDwiki가 뜰 것입니다.  외부의 다른 컴퓨터에서 접근하려면 이 서비스를 제공하는 현재 PC의 IP 주소와 포트번호 8000번을 이용하면 접속이 됩니다.  예를 들어 외부의 다른 컴퓨터 웹브라우저 주소창에 'http://123.45.67.89:8000' 이런 식으로 써주면 될 것입니다.

* 현재 내 PC의 아이피 주소를 확인하고 싶다면 `ifconif` 명령으로 확인해 볼 수 있습니다.  만일 VirtualBox에서 리눅스를 돌리고 있다면, 호스트쪽 윈도우에서 브라우저를 열어서 해당 주소와 포트넘버를 쳐넣어서 잘 뜨는지 확인해 볼 수 있습니다.

* 웹서버를 종료하고 싶으면,  `./miniWebServer.py 8000` 명령을 실행시켰던 터미널을 강제로 종료하거나 또는 'Ctrl+c'를 누르면 됩니다.
