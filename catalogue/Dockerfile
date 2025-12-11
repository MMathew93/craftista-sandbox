FROM python:3.14-alpine

RUN apk add --no-cache curl

WORKDIR /app/catalogue

COPY requirements.txt .

RUN pip install --no-cache-dir -r requirements.txt

COPY . .

CMD ["gunicorn", "app:app", "--bind", "0.0.0.0:5000"]
