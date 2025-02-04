FROM python:3.9-slim
WORKDIR /app
COPY /var/lib/jenkins/workspace/ecr/requirements.txt /var/lib/jenkins/workspace/ecr/requirements.txt
RUN pip install -r /var/lib/jenkins/workspace/ecr/requirements.txt
#COPY . .
CMD ["python", "app.py"]
