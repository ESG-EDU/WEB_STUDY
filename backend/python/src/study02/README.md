## python 알아보기

> 1. 파이썬 독립적인 개발 환경 만들기
```bash
python -m venv [폴더명]
```

- 프로젝트 폴더 구조 (Windows 기준)
```
project/
 ├─ venv/
 │   ├─ Scripts/
 │   ├─ Lib/
 │   └─ pyvenv.cfg
 ├─ main.py
```

- venv 활성화(Activate)
```bash
venv\Scripts\activate
```

- venv 비활성화(Deactivate)
```bash
deactivate
```

> 2. 파이썬 파일 실행 하기
```bash
python 파일.py
```
