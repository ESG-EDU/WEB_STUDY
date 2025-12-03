## FastAPI 알아보기

> 프로젝트 생성 (`uv`환경)

- 프로젝트 초기화
```bash
uv init [프로젝트명]
```

- `FastAPI` 패키지 추가
```bash
uv add fastapi --extra standard
```

- `main.py` 기본 정보 설정
```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
async def root():
    return {"message": "Hello World"}
```

- ***FastAPI + uv*** 실행 명령어 표

| 목적 | 명령어 | 설명 |
| :---: | :---: | :---: |
| FastAPI 설치 | `uv add fastapi` | FastAPI 패키지를 프로젝트에 설치 |
| Uvicorn 설치 | `uv add uvicorn` | FastAPI 실행용 ASGI 서버 설치 |
| 서버 실행 (기본) | `uv run uvicorn main:app` | `main.py` 안의 `app` 실행 |
| 자동 리로드 | `uv run uvicorn main:app --reload` | 코드 변경 시 자동 재시작 |
| 특정 host/port로 실행 | `uv run uvicorn main:app --host 0.0.0.0 --port 8000` | Docker/배포 환경에서 사용 |
| 모듈 실행 방식 | `uv run uvicorn myapp.main:app --reload` | 패키지 구조일 때 사용 |
| requirements 생성 | `uv export -o requirements.txt` | uv 프로젝트에서 pip용 파일 생성 |
| 가상환경 접속 | `uv venv` | uv가 만든 venv 생성(자동도 가능) |
| venv 안에서 명령 실행 | `uv run <command>` | 별도 활성화 없이 venv 명령 실행 |
