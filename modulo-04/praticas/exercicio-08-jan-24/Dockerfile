FROM python:alpine
WORKDIR /service
COPY . .
RUN pip install -r requirements.txt
EXPOSE 8080
ENTRYPOINT [ "python", "app.py" ]
