FROM python:3.12-slim

WORKDIR /app

# 1. copy dependency file
COPY pyproject.toml .

# 2. install dependencies
RUN pip install --no-cache-dir -r <(python - <<'PY'
import tomllib, sys, pathlib, textwrap
deps = tomllib.loads(pathlib.Path('pyproject.toml').read_text())['project']['dependencies']
print("\n".join(deps))
PY
)

# 3. copy the application code
COPY app ./app

CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]


