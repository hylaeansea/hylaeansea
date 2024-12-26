Use this to create rsa keys for the jupyter server

`openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout key.pem -out cert.pem`

Use this to build the docker image

`docker build --tag custom-jupyter . `

Use this to run the docker image

`docker run -d --gpus all -p 8888:8888 -v ./:/home/jovyan/work -e JUPYTER_ENABLE_LAB=yes --restart=always --name jupyter custom-jupyter`

This will run a jupyter notebook container on 0.0.0.0:8888 with the current directory mounted as /home/jovyan/work and lab enabled. The container will restart automatically if it crashes. The key to get access to the jupyter notebook is printed in the console inside the container when you run the docker run command. This token can be found by looking at the output of:

`docker logs jupyter 2>&1 | grep 'token=' | sed 's/.*token=//'`

The token will be output several times and can be used in the browser to log into the jupyter lab instance running at https://<hostname>:8888

