#AIDP 사용자 매뉴얼 작성방법 소개 

본 문서는 AIDP사용자 매뉴얼을 **작성하는 방법에 대해 안내**해 드립니다.
대상은 현재 AI/DT Engineering CoE중 AIDP **플랫폼을개발,운영하시는 구성원**이 대상입니다..


## 작성순서

개발(운영)을 담당하고 계시는 구성원들은 기존 TDE의 문서를 MD(MarkDown)문서로 변환하시거나 MD파일로 작성하셔서 AIDP github repository로 업로드 하시면됩니다.
업로드된 MD파일은 자동으로 Mkdocs서버의 특정 디렉토리에 sync되어 웹 화면으로 즉시(수초이내) 반영됩니다.
아래 몇가지 규칙에 따라 MD파일을 작성하시고 git으로 push하시면 됩니다.
(향후 기본적은 문서내용을 Tech write가 취합하여 체계에 맞게 구성하여 배포하는 체계가 필요하겠습니다)

## MD(Mark Down) 파일명

파일명과 디렉토리는 Tech Write가 목차를 사전 구성하여 각 개발 담당자에 알려드립니다.
개발자가 자유롭게 작성하여도 되나 문서의 목차구성과 문서 전체적인 일관성을 위해 사전 공유하여 진행합니다.
가령 **"VDI신청방법"**에 대해 담당하고 계신다면 Tech Writer는 사전 목차를 구성하고 **"VDI신청방법.md"로 파일명을 저장**하고 git으로 업로드하실것을 요청드릴겁니다. 
(Mkdocs.yml파일은 문서의 configuration을 저장하고 있는데 이 파일에 대해서 자동화하고 보다 편리하게 운영하는 방법에 대해 고민하고 있으며 개선할 예정입니다)

## TDE 문서 변환하기

현재 기존 문서들은 주로 TDE에 기록하고 있어 변환이 필요합니다.
**TDE화면에서 아래 그림처럼 exprt to word로 간단하게 docx파일로 export**하실 수 있습니다.
이후 아래 **pandoc명령으로 MD파일로 변환**이 가능합니다.
pandoc --extract-media ./vdi VDI신청방법.docx -o VDI신청방법.md
위 명령은 docx문서내의 이미지를 ./vdi/media에 추출하여 저장합니다
(**pandoc는 각 개발자 환경에 따라 설치** 하셔야 합니다. linux ubuntu의 경우 간단하게 sudo apt-get install pandoc으로 설치가 가능합니다)


## git push

작성하신 파일을 git repository로 업로드하는 명령은 이미 익숙하실겁니다.
업로드하시기전에 약간의 수정이 필요하다면 MD파일 에디터를 사용하여 수정 하며 특정 MD파일 에디터에서는 githup 연계가 되는 에디터도 있습니다
개인의 환경에 맞게 선택하여 사용하시면 될 것 같습니다.
일반적인 순서에 대해 부연설명드립니다
1) git init
2) git add ./시작하기/VDI신청방법.md
3) git commit -m "VDI신청방법 오타수정"
4) git push aidp-doc-repo master
(현재 repository는 테스트 환경에서 구성되었고 테스트 완료 후 작성된 문서를 포함하여,향후 일괄적으로 안정적 시스템에 이관할 예정입니다)
[https://github.com/kyoungyunkim/doc_test1](https://github.com/kyoungyunkim/doc_test1)
user/password : kyoungyunkim / ************** (별도 공유)

## Github - jenkins

CI환경에서 많이 사용하는 github의 webhook을 이용하여 jenkins의 build(git pull)을 하는 형태로 구성했습니다.
jenkins를 사용한것은 MKDocs에 개발자가 수정하고 git으로 반영시 즉각적으로 반영되고 각 개별담당자별로 업데이트 되는 내용을 바로 반영할 수 있는 장점은 있습니다.
향후에는 문서 배포에 있어 별도의 검토절차가 필요할것 같습니다


## MKDocs

jenkins를 통해 업데이트된 문서를 git pull하여 웹화면으로 즉시 반영합니다.
mkdocs.yml파일이 문서의 전체적 구성정보를 가지고 있는 파일로,목차나 문서의 네비게이션,템플릿등을 적용해 줍니다.
서두에 말씀드린 목차 구성에 있어서 개발자들이 자유롭게 문서명등을 정해서 업로드해도 되나 AIDP를 사용하는 사용자(분석가)입장에 보다 쉽게 직관적으로 이해할 수 있도록 목차나 내용을 구성하는것이 중요할것 같아 다소 불편하더라도 이 부분은 현재 수동으로 구성하고 있습니다만 다를 내용은 많지 않아 작성에 있어 비용이 들지 않을 것 같습니다.(향후 개선이 필요한 부분입니다.)

# 작성 flow

![enter image description here](http://18.219.180.88:9000/image/guide/image1.png)

