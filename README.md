# FastAPI in Docker example
[From FastAPI site](https://fastapi.tiangolo.com/deployment/docker/)
>Docker is a software platform that allows you to build, test, and deploy applications quickly.   
Docker packages software into standardized units called containers that have everything  
the software needs to run including libraries, system tools, code, and runtime.
### Project structure
``` bash
    ├── app
    │   ├── __init__.py
    │   └── app.py
    ├── .gitignore
    ├── Dockerfile
    ├── README.md
    ├── main.py
    └── requirements.txt
```

## Without docker
### Setup the project
```bash
pip install -r requirements.txt
```

### Run
```bash
uvicorn main:app --host 0.0.0.0 --port 8000
```

### Check
1. http://127.0.0.1:8000/
```
Hello	"FastApi in Docker test"
```

2. http://127.0.0.1:8000/items/5?q=somequery
```
item_id	5
q	"somequery"
```

3. http://127.0.0.1:8000/docs


## Docker
Maybe run as sudo
### Build
``` bash
docker build -t fastdoc .
```

### Run
``` bash
docker run -d --name fastdoc -p 80:80 fastdoc

docker container stop fastdoc
fastdoc

docker container sart fastdoc
fastdoc
```


### Check
1. http://127.0.0.1/
```
Hello	"FastApi in Docker test"
```

2. http://127.0.0.1/items/5?q=somequery
```
item_id	5
q	"somequery"
```

3. http://127.0.0.1/docs



### Some useable Docker commands
1. View image:
```bash
docker image ls
REPOSITORY    TAG       IMAGE ID       CREATED         SIZE
fastdoc       latest    177ca8c9a42c   6 seconds ago   868MB
```
2. View container:
```bash
docker container ls
CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS
02aada22a754   fastdoc   "uvicorn app.app:app…"   20 seconds ago   Up 19 seconds
```
3. Remove container:
```bash
docker container rm fastdoc
fastsoc
```
4. Remove image:
```bash
docker image rm fastdoc
Untagged: fastdoc:latest
Deleted: sha256:177ca8c9
```
