FROM python:3.9.18-slim-bookworm

WORKDIR /python-docker

COPY requirements.txt .
RUN pip3 install -r requirements.txt

COPY . .

RUN apt-get update && apt-get install -y unzip && \
    mkdir -p /usr/local/share/nltk_data/sentiment && \
    unzip -o sentiment/vader_lexicon.zip -d /usr/local/share/nltk_data/sentiment && \
    rm -rf /var/lib/apt/lists/*

ENV NLTK_DATA=/usr/local/share/nltk_data

CMD ["python3", "-m", "flask", "run", "--host=0.0.0.0", "--port=5000"]
