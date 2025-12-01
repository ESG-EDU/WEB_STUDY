# 파이썬 기초 교육

## 파이썬 시작하기

> 1. 파이썬 설치

- [공식](https://www.python.org/downloads/)
- [Anaconda](https://www.anaconda.com/)

> 2. `venv`: 독립적인 개발 환경 만들기

```bash
python -m venv venv
```

> 3. `uv`: 패키지 관리 도구 ([`UV`](https://docs.astral.sh/uv/))

- `MacOS` 또는 `Linux`
```bash
curl -LsSf https://astral.sh/uv/install.sh | less
```

- `Windows`
```bash
powershell -c "irm https://astral.sh/uv/install.ps1 | more"
```

- `pip` 설치
```bash
pip install uv
```
---

## 파일 확장명
+ Python 파일: `*.py`
+ Jupyter Notebook: `*.ipynb`

## 파이썬의 철학

```python
import this
```
