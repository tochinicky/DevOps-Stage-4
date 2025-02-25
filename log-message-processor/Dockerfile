# Build stage
FROM python:3.9-alpine AS builder

RUN apk add --no-cache g++ musl-dev python3-dev libffi-dev libressl-dev
COPY requirements.txt .
RUN pip install --user -r requirements.txt

# Runtime stage
FROM python:3.9-alpine
COPY --from=builder /root/.local /usr/local
COPY . .
CMD ["python", "main.py"]