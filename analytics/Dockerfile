FROM public.ecr.aws/docker/library/python:3.10-alpine

RUN mkdir /app
WORKDIR /app

RUN adduser -u 1000 -D app
USER app
COPY . /app
RUN pip install -r requirements.txt

CMD python app.py
