FROM ubuntu:18.04

# add files to required directories
ADD README.md /
ADD print_hello.sh /bin

RUN apt-get update && \
     apt-get install -y cmake build-essential python3 python3-pip

COPY . ./cmake-project
WORKDIR ./cmake-project

RUN cmake . && cmake --build .

RUN useradd -ms /bin/bash devops2022user
USER devops2022user

RUN pip3 install -r requirements.txt

EXPOSE 8898

ENTRYPOINT ["python3", "app.py", "--port", "8898", "--host", "0.0.0.0"]
