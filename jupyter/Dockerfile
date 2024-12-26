FROM jupyter/base-notebook:latest

USER root

RUN pip install numpy torch

COPY cert.pem key.pem /home/jovyan/work
COPY jupyter_lab_config.py /home/jovyan/.jupyter/

EXPOSE 8888

CMD ["start.sh", "jupyter", "lab"]
