# pip

django 프로젝트를 진행하면서 모듈 설치를 할 일이 많았기에 `pip install`을 많이 사용했다.

그런데 문서를 참고하다 보면 대게 `python -m pip install`이런 식으로 작성해 놓은 문서가 많이 있다.

그래서 둘의 차이를 알아보았다.

## pip install

`pip install`은 Python package 관리자인 pip를 직접 실행하는 명령어다. 이 명령어를 사용하면 시스템에 설치된 Python interpreter에서 pip를 실행하여 설치한다.

## python -m pip install

`python -m`은 Python interpreter 모듈을 실행하는 명령어다. `-m` 뒤에 모듈 이름을 지정하고, 해당 모듈을 Python interpreter로 실행한다.

## 정리

일반적으로 둘 다 동일한 결과를 가져오지만, venv에서 사용할 때는 `python -m pip install`을 사용하는 것이 권장된다.

이렇게 하면 가상 환경에 연결된 해당 Python interpreter에서 pip 를 실행하여 패키지를 설치할 수 있다.

추가적으로 `python -m pip install`을 사용하면 Python interpreter 모듈을 직접 실행하기 때문에, 버전이나 경로에 대한 문제를 방지할 수 있다.

따라서 일반적인 사용 시에도 `python -m pip install`을 사용하는 것이 안정적이고 권장 되는 방법이다.