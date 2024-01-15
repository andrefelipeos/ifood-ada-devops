FROM python:alpine
WORKDIR /service
RUN pip install flask flask-sqlalchemy flask-login
COPY . ./
ENV FLASK_APP=project
EXPOSE 5000
CMD [ "flask", "run", "--host=0.0.0.0" ]
