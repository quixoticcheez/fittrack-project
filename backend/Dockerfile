FROM python:3.12-slim

WORKDIR /app

# copy dependency file
COPY pyproject.toml .

# install dependencies
RUN pip install --no-cache-dir fastapi "uvicorn[standard]"

# copy application code
COPY app ./app

CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]

