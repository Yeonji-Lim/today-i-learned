# pre-commit으로 flake8, black 적용하기

## pre-commit 설치

```
pip install pre-commit

# or

brew install pre-commit
```

## 설정 파일 생성

```
pre-commit sample-config > .pre-commit-config.yaml
```

내용에 black과 flake8 관련 내용 추가

```yaml

# See https://pre-commit.com for more information

# See https://pre-commit.com/hooks.html for more hooks

repos:

	- repo: https://github.com/pre-commit/pre-commit-hooks
		
		rev: v3.2.0
		
		hooks:
			
			- id: trailing-whitespace
			
			- id: end-of-file-fixer
			
			- id: check-yaml
			
			- id: check-added-large-files
	
	- repo: https://github.com/psf/black
		
		rev: stable
		
		hooks:
			
			- id: black
		
		language_version: python3.8
	
	- repo: https://github.com/PyCQA/flake8
		
		rev: 4.0.1
		
		hooks:
			
			- id: flake8

```

## autoupdate
```
pre-commit autoupdate
```

## 자동화

```
pre-commit install
```