FROM python:3.8-slim-bookworm

LABEL maintainer="ons lahmar"

WORKDIR /app

COPY requirements.txt .

RUN apt-get update && apt-get install -y \
    build-essential \
    libldap2-dev \
    libsasl2-dev \
    && rm -rf /var/lib/apt/lists/*

RUN pip install --no-cache-dir -r requirements.txt

COPY student_age.py .
RUN mkdir -p /data
COPY student_age.json /data/student_age.json

ENV student_age_file_path=/data/student_age.json

EXPOSE 5000

CMD ["python", "student_age.py"]
