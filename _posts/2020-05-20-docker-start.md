---
layout: single
title: Docker 란 무엇인가?
excerpt: 로고가 귀여운게 생존에 어떤 도움이 되는지 확실히 보여주는 도커를 알아보자.
categories: docker
tags: docker
---

# Docker 란?
![docker logo](../public/uploads/2020-05-20-docker-start/000.png)

# Docker 기본 명령어

## 1. 이미지 가져오기
> 일단 가져오고 하고 싶은 이미지의 이름을 알아야 한다.  
> 만약 이미지 이름과 버전을 알고 있다면 다음 양식처럼 이미지를 가져올 수 있다.  
> REPOSITORY 는 이미지의 이름, TAG 는 이미지의 버전이다.
> ``` bash
> root@root:~# docker pull REPOSITORY:TAG
> ```
> 가져오고 싶은 이미지의 이름을 모르거나 docker 에서 제공하는지 모르겠다면  
> [Docker Hub]("https://hub.docker.com/") 에서 검색을 해서 찾으면 된다.  
> [Docker Hub]("https://hub.docker.com/") 에서 이미지를 찾는 방법은  
> 
> ![how to use docker hub 001](../public/uploads/2020-05-20-docker-start/001.png)
> 
> Docker hub 사이트에 접속한 후 (가입은 자유)
> 
> ![how to use docker hub 002](../public/uploads/2020-05-20-docker-start/002.png)
> 
> 원하는 이미지를 검색한다.
> 
> ![how to use docker hub 003](../public/uploads/2020-05-20-docker-start/003.png)
> 
> 그럼 검색된 목록이 보이는데 여기서 배포자를 확인하거나  
> 이미지의 상세 항목을 확인한 후 원하는 이미지를 선택하면 된다.  
> 필자는 ubuntu 에서 정식 배포한 이미지면서 아무런 추가 기능이 없는  
> 이미지를 가져오기 위해서 다음 항목을 선택했다.
> 
> ![how to use docker hub 004](../public/uploads/2020-05-20-docker-start/004.png)
> 
> 그럼 다음과 같은 상세 페이지가 보인다.
> 
> ![how to use docker hub 005](../public/uploads/2020-05-20-docker-start/005.png)
> 
> 여기서 마지막 버전을 가져오고 싶다면 아래 이미지에 표시된 영역의 코드를 복사하면 된다.
> 
> ![how to use docker hub 006](../public/uploads/2020-05-20-docker-start/006.png)
> 
> 하지만 특정 버전이나 LTS 버전같이 버전을 선택해서  
> 가져오고 싶다면 다음 이미지와 같이 Tag 탭으로 이동한다.
> 
> ![how to use docker hub 007](../public/uploads/2020-05-20-docker-start/007.png)
> 
> 그러면 배포된 모든 버전을 확인할 수 있다.  
> 여기서 원하는 버전을 선택해서 pull 코드를 복사하면 된다.
> 
> ![how to use docker hub 008](../public/uploads/2020-05-20-docker-start/008.png)
> 
> 그리고 터미널에서 복사한 코드를 실행하면 된다.
> ``` bash
> root@root:~# docker pull ubuntu:18.04
> ```
> 실행을 하면 이미지를 다운로드 하는 모습이 보인다.  

## 2. 이미지 목록 조회
> 다운로드한 이미지 목록을 보는 명령어는 간단하다.
> ``` bash
> root@root:~# docker images
> ```
> 입력하게 되면 목록이 보여지는데 다음과 같다.
> |TITLE        |DESCRIPTION            |
> |-------------|-----------------------|
> |REPOSITORY   |이미지의 이름          |
> |TAG          |이미지의 버전          |
> |IMAGE ID     |이미지의 고유 아이디   |
> |CREATED      |이미지를 가져온 날짜   |
> |SIZE         |이미지의 용량          |
> 이미지 목록 조회에서는 옵션에 대한 설명은 생략한다.  
> 굳이 옵션까지 설명하지 않더라도 충분한 정보를 조회할 수 있기 때문에  
> 만약 이미지 목록 조회에 대한 옵션에 대해서 궁금한 사용자는  
> [Docker Images Reference](https://docs.docker.com/engine/reference/commandline/images/) 를 확인하길 추천한다.

## 3. 컨테이너 생성
> 개인적으로 docker 명령어의 꽃이다. 옵션이 정말정말 많다.  
> 다 외울 생각하지 말고 그냥 문서 보면서 만드는게 정신건강에 이롭다.  
> 아무 옵션없이 실행하는 명령어를 일단 확인해보자.
> ``` bash
> root@root:~# docker run REPOSITORY:TAG
> ```
> 또는 이미지의 고유 아이디로도 컨테이너 생성이 가능하다.
> ``` bash
> root@root:~# docker run IMAGE ID
> ```
> 이렇게 작성해주면 docker 컨테이너가 하나 만들어지고 실행된다.  
> 하지만 사실 이렇게 실행하면 컨테이너가 하나일 때는 문제가 되지 않지만  
> 컨테이너가 여러개라면 문제가 발생하기 시작한다.  
> 예를 들어 포트를 80 과 443 포트를 사용하는 컨테이너 하나를 생성했다고 가정해보겠다.  
> 그리고 또 80 포트와 443 포트를 사용하는 컨테이너를 하나 더 생성했다고 가정해보겠다.  
> 80 포트로 접속을 하면 어떤 컨테이너를 보여줘야 하는가?  
> 그래서 컨테이너 외부 포트와 컨테이너 내부 포트를 나눠서 맵핑해야 관리가 편하다.  
> 컨테이너 생성하는 옵션들은 대부분이 위의 예제처럼 맵핑에 관련된 옵션들이다.  
> 그럼 이제 옵션들을 하나씩 차근차근 알아보기 싫다...  
> 그러니 자주 쓰이는 몇 개만 살펴보록 하겠다.  
> 그 외에는 검색해서 그때그때 옵션들을 확인하는 것을 추천한다.
> 
> ### ***--name***
> 컨테이너 이름을 지정할 때 사용하는 옵션.  
> 왠만하면 이름을 지정하는 것을 추천한다.  
> 안그러면 이미지 고유 아이디처럼 컨테이너도 고유 아이디가 생성되는데  
> 이름을 지정하지 않는다면 고유 아이디로 컨테이너에 접근을 해야한다.  
> 처음에 한 두개 있을때는 모르겠지만 여러개의 컨테이너를 관리할 때  
> 이름을 하나도 지정하지 않으면 나중에는 어떤게 어떤 컨테이너인지 구분하기 힘들어진다.
> 
> ### ***-d*** 또는 ***--detach***
> 컨테이너를 데몬 모드, 즉 백그라운드에서 실행하는 옵션  
> 컨테이너를 실행하는데 짧은 시간이 걸리면 상관 없지만  
> 컨테이너를 실행하는데 오랜 시간이 걸릴때 데몬 모드로 실행하지 않으면  
> 컨테이너가 실행될때까지 아무것도 못하고 실행되는 로그를 바라봐야 한다.
> 
> ***-d 옵션을 사용하지 않은 모습***  
> [![docker run without detach option](https://img.youtube.com/vi/H_HCvY3xpmw/0.jpg)](https://youtu.be/H_HCvY3xpmw)  
> ***이미지 클릭하면 youtube 영상으로 이동***  
> 
> 영상은 10배속으로 편집한 모습이다.  
> 실제로는 20분이 넘게 지속되다가 이정도면 충분하다고 생각되어 중단했다.  
> 다시 말하지만 중.단.했다.
> 
> ***-d 옵션을 사용한 모습***  
> [![docker run without detach option](https://img.youtube.com/vi/tILPJPkcteU/0.jpg)](https://youtu.be/tILPJPkcteU)  
> ***이미지 클릭하면 youtube 영상으로 이동***  
> 
> 영상은 재생속도를 편집하지 않았다.  
> 
> 위의 예제로 알 수 있듯이 ***--detach*** 옵션을 사용하면  
> 백그라운드에서 컨테이너가 실행되는 동안 다른 작업을 진행할 수 있다.
> 
> ### ***-i*** 또는 ***--interactive***
> 상호 입출력.
> 
> ### ***-t*** 또는 ***--tty***
> tty를 활성화하여 bash 쉘을 사용.  
> 
> #### ***-i & -t 각주***
> 터미널에서 접속해서 bash shell 을 사용하려는 경우  
> ***-i*** 와 ***-t*** 옵션을 기본적으로 추가해서 사용한다.
> 
> ### ***-p 또는 --publish***
> 컨테이너 외부 포트와 컨테이너 내부 포트를 맵핑하는 옵션.  
> ``` bash
> root@root:~# docker run -p OUTER_PORT:INNER_PORT
> ```
> 여러 포트를 맵핑하는 경우에는 반복적으로 옵션을 설정하면 된다.
> ``` bash
> root@root:~# docker run -p OUTER_PORT:INNER_PORT -p OUTER_PORT:INNER_PORT
> ```
> 
> ### ***-h*** 또는 ***--hostname***
> 컨테이너 host name 을 설정하는 옵션.  
> 일반적으로는 크게 차이가 없지만  
> 어떤 이미지는 hostname 을 설정해야 하는 경우도 있다.
> 
> ### ***--restart***
> 컨테이너가 종료되었을때 재시작 정책을 설정하는 옵션.
> ``` bash
> --restart no            # 컨테이너가 종료되더라도 재시작되지 않는 옵션.
> --restart on-failure:10 # 컨테이너가 종료되면 자동으로 재시작되고 재시작 시도 횟수를 지정할 수 있는 옵션.
> --restart always        # 컨테이너가 종료되면 자동으로 재시작을 시도하는 옵션.
> ```
>
> 여기까지가 필자가 자주 사용하는 ***docker run*** 옵션들이다.  
> 이외에도 많은 옵션을 제공하니 run 에 대해서 다른 옵션이 궁금하다면  
> [Docker Run Reference](https://docs.docker.com/engine/reference/run/) 를 한 번 읽어보는 것을 추천한다.  
> 필자가 자주 사용하는 옵션까지 사용한 run 코드의 형태는 다음과 같은 모양이 된다.
> ``` bash
> root@root:~# docker run -itd \
> > --name test
> > --hostname test.nextculture.kr \
> > --publish 10100:22 \
> > --publish 10101:3306 \
> > --publish 10102:6379 \
> > --publish 10103:8443 \
> > --publish 10104:8444 \
> > --publish 10105:8445 \
> > --restart always \
> > ubuntu:18.04
> ```

## 4. 컨테이너 생성 및 실행
> 이 부분은 사실 run 을 사용하면 사용할 일이 적지만 그래도 알고 있으면  
> 활용할 수 있는 여지가 있기때문에 이런게 있다 정도는 알고 있는게 좋을 것 같다.
> 
> ### 컨테이너 생성
> 
> ``` bash
> root@root:~# docker create [options...]
> ```
> run 명령과 옵션은 동일하다.  
> 실행이 되지 않는 차이만 있다.  
> 
> ### 컨테이너 실행
> 
> ``` bash
> root@root:~# docker start NAMES OR CONTAINER ID
> ```
> 컨테이너의 고유 이름 또는 고유 아이디로 컨테이너를 실행할 수 있다.

## 5. 컨테이너 접근하기
> Ubuntu 컨테이너를 생성했다면 이제 Docker 가 아닌  
> 생성한 Ubuntu 내부에 접속해서 설정을 해야하는데  
> 물론 이미지마다 설치된 항목들이 다르겠지만  
> SSH 도 설치가 안된 상황이라면 터미널로 접근할 수도 없으니  
> Docker 에서 바로 접근하는 방법을 알아보자.
> ``` bash
> root@root:~# docker exec -it [NAMES OR CONTAINER ID] [COMMAND]
> ```
> 위의 코드와 같이 컨테이너의 고유 정보 외에도 컨테이너 기본 명령어를 작성해줘야 한다.  
> 만약 기본 명령어가 뭔지 모른다면 [7. 컨테이너 목록 조회](#7.-컨테이너-목록-조회) 를 참고한다면 확인할 수 있다.  
> 
> 여기서 사용한 ***-i*** 와 ***-t*** 옵션은 run 에서 사용한 옵션과 동일하다.  
> run 에서 사용한 옵션과 다른 옵션도 있지만 잘 사용되지 않는다.  
> 만약 다른 옵션이 궁금하다면 [Docker Exec Reference](https://docs.docker.com/engine/reference/commandline/exec/) 를 참고하길 바란다.

## 6. 이미지 생성
> 컨테이너를 만들고 만들어진 컨테이너의 설정이 이전에 만든 컨테이너와 동일할 경우가 있다.  
> 이때 똑같은 이미지를 사용해서 컨테이너를 만들고 똑같은 설정을 반복하게 되는데  
> 이 과정이 정말 똑같거나 흡사해서 중복되는 항목들을 매번 설정하는 것에 대해서  
> 생산성이 굉장히 안좋다고 느껴질 수 있다.  
> 백번 공감할 수 있는 내용이고 이 부분을 해결하기 위해  
> 이미 있는 이미지가 아닌 컨테이너의 현재 상태 그대로 이미지화 시킬 수 있다.  
> 이미지를 생성하는 것은 위의 글처럼 중복되는 항목들을 미리 설정해서  
> 같은 설정을 반복하지 않기 위하여 이미지를 생성할 수도 있고,
> 백업을 위해서 생성할 수도 있으며 배포를 위해서 생성할 수도 있다.  
> 예를 들어 SSH 설정과 Apache 설정 그리고 Java 11 을 설정한 Ubuntu 컨테이너를 만들었다고 가정을 해보겠다.  
> 똑같은 설정을 해줘야 하는 상황이 발생한다면 이미 만들어진 위의 컨테이너를 이미지로 만들어서  
> 만들어진 이미지로 컨테이너를 생성한다면 똑같은 설정을 가진 컨테이너를 한 줄의 명령어로 복제할 수 있다.  
> 그래서 이 부분은 생산성 향상에 도움이 되기때문에 꼭 읽어보길 추천한다.  
> 컨테이너까지는 만들었다는 전제하에 진행을 하도록 하겠다.  
> ``` bash
> root@root:~# docker commit [NAMES OR CONTAINER ID] [REPOSITORY[:TAG]]
> ```
> 컨테이너를 이미지로 만들때 대상 컨테이너의 고유 아이디나 이름이 필요하고  
> 만들어질 이미지의 이름과 버전이 필요하다.  
> 그 외의 옵션은 선택항목이기 때문에 [Docker Commit Reference](https://docs.docker.com/engine/reference/commandline/commit/) 를 확인하고 작성하는 것을 추천한다.  
> 생성할 이미지를 docker hub 에 배포하는 방법에 대해서는  
> 도커에 대한 기본 설명이 아니라고 판단되어 다른 포스팅에서 설명하도록 하겠다.

## 7. 컨테이너 목록 조회
> 컨테이너 목록을 조회할 때도 옵션이 몇 가지 있다.  
> 기본적인 명령어는 아래 모습과 같다.  
> ``` bash
> root@root:~# docker ps
> ```
> 이때 보여지는 항목으로는  
> |TITLE        |DESCRIPTION                            |
> |-------------|---------------------------------------|
> |CONTAINER ID |컨테이너의 고유 아이디                 |
> |IMAGE        |컨테이너 생성에 사용된 이미지          |
> |COMMAND      |컨테이너 시작할 때 실행될 기본 명령어  |
> |CREATED      |컨테이너 생성 날짜                     |
> |STATUS       |컨테이너 상태                          |
> |PORTS        |컨테이너에서 사용하고 있는 포트 목록   |
> |NAMES        |컨테이너의 고유 이름                   |
> 하지만 위의 명령어는 실행중인 컨테이너의 목록만 보여준다.  
> 
> ### ***-a 또는 --all***
> 이 옵션은 중지된 컨테이너 목록까지 보여준다.
> 
> ### ***-f 또는 --filter***
> 이 옵션은 컨테이너를 색인해서 목록을 보여준다.  
> 색인할 수 있는 항목에 대해서는 [Docker PS Filtering](https://docs.docker.com/engine/reference/commandline/ps/#filtering) 를 확인하면 자세히 나와있으니 참고바란다.
> 
> ### ***--format***
> 이 옵션은 목록에서 보여지는 항목을 지정할 수 있다.  
> 자세한 항목에 대한 설명은 [Docker PS Formatting](https://docs.docker.com/engine/reference/commandline/ps/#formatting) 를 확인하면 자세히 나와있으니 참고바란다.
> 
> ### ***-n 또는 --last 그리고 숫자***
> 아래 예제를 예로 들어 설명하도록 하겠다.
> ``` bash
> root@root:~# docker ps -n 3
> ```
> 위의 코드처럼 사용하면 마지막으로 생성된 컨테이너 3 개의 목록을 보여준다.  
> 숫자 부분은 다른 숫자로 대체 가능하다.
> 
> ### ***-l 또는 --latest***
> 이 옵션을 사용하면 가장 마지막에 생성한 컨테이너 하나만 보여진다.
> 
> ### ***--no-trunc***
> 컨테이너 고유 아이디는 원래 긴 문자열인데  
> 화면에 표시될 때 길어서 불편하므로 짧은 이름으로 표시된다.  
> 이 옵션을 사용하면 고유 아이디가 원래 이름으로 표시된다.
> 
> ### ***-q 또는 --quiet***
> 이 옵션은 숫자 아이디만 보여준다.
> 
> ### ***-s 또는 --size***
> 이 옵션 컨테이너의 용량까지 보여준다.
> 
> 필자가 자주 사용하는 옵션까지 사용한 ps 코드의 형태는 다음과 같은 모양이 된다.
> ``` bash
> root@root:~# docker ps --no-trunc --format "{{.Names}} : {{.Status}} : {{.Command}} : {{.Image}}"
> ```

## 8. 컨테이너 중지
> ``` bash
> root@root:~# docker stop NAMES OR CONTAINER ID
> ```
> 컨테이너의 고유 이름 또는 고유 아이디로 컨테이너를 중지할 수 있다.

## 9. 컨테이너 삭제
> ``` bash
> root@root:~# docker rm NAMES OR CONTAINER ID
> ```
> 컨테이너의 고유 이름 또는 고유 아이디로 컨테이너를 삭제할 수 있다.  
> 이때 컨테이너는 중지된 상태여야 삭제가 가능하다.

## 10. 이미지 삭제
> ``` bash
> root@root:~# docker rmi REPOSITORY:TAG OR IMAGE ID
> ```
> 이미지의 이름과 버전 또는 고유 아이디로 이미지를 삭제할 수 있다.  
> 이때 삭제하려는 이미지를 사용해서 생성된 컨테이너가 없어야 삭제가 가능하다.  
> 그래서 이미지를 삭제할 때 삭제할 이미지를 사용하는 모든 컨테이너도 삭제하는 옵션이 있다.
> ``` bash
> root@root:~# docker rmi -f REPOSITORY:TAG OR IMAGE ID
> ```

## 11. 그 외의 도커 명령어
> 지금까지 설명한 11 개의 명령어를 제외하더라도 많은 명령어가 존재한다.  
> 지금까지 설명한 것만으로도 필자는 개발 서버정도는 충분히 관리가 가능했다.  
> Docker 로 실제로 외부 사용자에게 서비스를 해본적은 없기때문에  
> 위의 명령어로 충분하다고 장담할 수는 없다.  
> 그래서 [Docker CLI Reference](https://docs.docker.com/engine/reference/run/) 를 시간이 된다면 한 번 읽어보는 것을 추천한다.