# # Build stage
# FROM python:3.9-alpine AS builder

# RUN apk add --no-cache g++ musl-dev python3-dev libffi-dev libressl-dev
# COPY requirements.txt .
# RUN pip install --user -r requirements.txt

# # Runtime stage
# FROM python:3.9-alpine
# COPY --from=builder /root/.local /usr/local
# COPY . .
# CMD ["python", "main.py"]

# Build stage
FROM python:3.9-alpine AS builder

RUN apk add --no-cache g++ musl-dev python3-dev libffi-dev libressl-dev
WORKDIR /app
COPY requirements.txt .
RUN pip install --prefix=/install -r requirements.txt

# Runtime stage
FROM python:3.9-alpine
WORKDIR /app
COPY --from=builder /install /usr/local
COPY . .

CMD ["python", "main.py"]