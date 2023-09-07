
FROM python:3.9-slim
COPY --from=openjdk:8-jre-slim /usr/local/openjdk-8 /usr/local/openjdk-8

ENV JAVA_HOME /usr/local/openjdk-8

RUN update-alternatives --install /usr/bin/java java /usr/local/openjdk-8/bin/java 1

RUN python3 -m pip install --upgrade pip setuptools wheel  

COPY requirements.txt /opt/app/requirements.txt

WORKDIR /opt/app

RUN python3 -m pip install -r requirements.txt

COPY . /opt/app

CMD [ "gunicorn", "app:app"]

