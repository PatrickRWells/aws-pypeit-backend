FROM continuumio/miniconda3:latest

RUN apt-get update && \
    apt-get -y install gcc mono-mcs curl unzip && \
    rm -rf /var/lib/apt/lists/*


RUN curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
RUN unzip awscliv2.zip
RUN ./aws/install

RUN apt-get install git
RUN git clone https://github.com/profxj/ginga
RUN cd ginga && python setup.py install

RUN pip install linetools
RUN pip install git+https://github.com/pypeit/PypeIt.git
RUN pip install -r /opt/conda/lib/python3.7/site-packages/pypeit/requirements.txt
RUN pip install boto3

ADD fetch_and_run_python.sh /usr/local/bin/fetch_and_run_python.sh

ENTRYPOINT ["/usr/local/bin/fetch_and_run_python.sh"]
