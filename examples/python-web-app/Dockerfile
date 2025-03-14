FROM ubuntu

# working dir for our project is /app
WORKDIR /app

# copy them to work dir
COPY requirements.txt /app/
COPY devops /app/          # copies S-code to work dir

RUN apt-get update && apt-get install -y python3 python3-pip python3-venv

SHELL ["/bin/bash", "-c"]

RUN python3 -m venv venv1 && \
source venv1/bin/activate && \
pip install --no-cache-dir -r requirements.txt    # installs dependencies from the req.txt

EXPOSE 8000

CMD source venv1/bin/activate && python3 manage.py runserver 0.0.0.0:8000




