FROM python:3.10-slim

WORKDIR /app

COPY . .

RUN pip install --upgrade pip && \
    pip install -r requirements.txt

CMD ["sh", "-c", "python app/main.py && test/pytest"]
